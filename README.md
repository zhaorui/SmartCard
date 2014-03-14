SmartCard
=========

All the experince  of mine in SmartCard area 

How to use pcscd to debug smartcard
=========
pcscd  is  the  daemon  program  for  pcsc-lite  and  musclecard framework. It is a
resource manager that coordinates communications with smart-card readers and  smart
cards and cryptographic tokens that are connected to the system.

pcscd would automatically start at boot time from /System/Library/StartupItems/SmartCard-Services.
Running "ps -ef | grep pcscd", we could see "pcscd -f" is running.
pcscd also would be stared when connecting the smartcard reader to computer.

Before use pcscd to debug, we need to close the running "pcscd -f" process first.
Then run command below to get a detailed APDU log to the terminal.

arch -i386 pcscd -f -d -a

To filter the APDU log from the detailed log, we should run command below
arch -i386 pcscd -f -d -a | egrep "APDU|SW"


How to build the Tokend in Mac
=========
1. Whatis TokenD?
2. What's the use of Tokend? (What's are the benefits of Using Tokend )
3. How can I build it?

A Tokend component is  provided to extend cryptographic support to Apple native
applications (Safari, Mail, Logon) as well as for 3rd party applications relying on the
Tokend cryptographic architecture (the Mac version of Microsoft Office, for example).
In a nutshell, it's like a driver in application level.

The reasons of using tokend listed below
1. View the contents of your smart card using Keychain Access
2. Lock or unlock the smart card keychain
3. Log on to a Mac using the IDPrime .NET smart card
4. Use the Safari browser to view secure web sites
5. Use Mail (Mac’s native e-mail program) to encrypt and/or digitally sign a message

To build a Tokend project using xcodebuild way is easy, Pl. look at the command below

xcodebuild -configuration Debug -arch x86 _ 64 build

a few make error would happend while building at Mac OS 10.8.3, but they're all easy to fix.
Using darwinbuild to build the project is troublesome, I give up that way.

Useful website to begin smartcard development
=========
Explaining U.S. Government Smart Cards
http://community.centrify.com/t5/The-Centrify-Apple-Guys/Explaining-U-S-Government-Smart-Cards/ba-p/11654

Smartcard service official site
https://smartcardservices.macosforge.org

Basic Knowledgement of smartcard site
http://www.cardwerk.com

Apple Open Souce of TokenD
http://opensource.apple.com/tarballs/Tokend/

Inter-network of caterpilla about Build CACNG
https://caterpillar.centrify.com/cims/Building_Tokend_for_Mac?highlight=%28build%29%7C%28tokend%29


