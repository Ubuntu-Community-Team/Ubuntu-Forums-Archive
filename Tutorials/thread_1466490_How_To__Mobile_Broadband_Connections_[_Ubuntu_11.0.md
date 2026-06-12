---
title: "How To : Mobile Broadband Connections [ Ubuntu 11.04 : 10.10 : 10.04 : 9.10]"
date: 2010-04-30
forum: Tutorials
---

### Post by alexfish on 2010-04-30
**[SIZE=2]11.04 users: [/SIZE]****[SIZE=2] First[/SIZE]****[SIZE=2] read post[/SIZE]** #[**59**]("http://ubuntuforums.org/showpost.php?p=11443633&postcount=59") 
[FONT=Verdana][SIZE=2][B]
Upgraded to [/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]**Natty**[/SIZE][/FONT][FONT=Verdana][SIZE=2]**: Network Manager not connecting any more, check this out: Post **[/SIZE][/FONT]  #[**2**]("http://ubuntuforums.org/showpost.php?p=10736509&postcount=2")
[FONT=Verdana][SIZE=2]**Natty **[/SIZE][/FONT][FONT=Verdana][SIZE=2]**new install **[/SIZE][/FONT][FONT=Verdana][SIZE=2]**:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]**read through this "first" post :**[/SIZE][/FONT][SIZE=2][FONT=Verdana]**(if device is not recognized) :**[/FONT][/SIZE][FONT=Verdana][SIZE=2]** note the reference to USB_MODESWITCH >**[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Natty users: **[/SIZE][/FONT][SIZE=2][FONT=Verdana]**and the link**[/FONT][/SIZE] 

**Keep in touch**
[http://www.canonical.com/about-canonical/overview](http://www.canonical.com/about-canonical/overview)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[FONT=Verdana][SIZE=2]** New Devices , RE: next generation , can have a look here **[/SIZE][/FONT]#[**59**]("http://ubuntuforums.org/showpost.php?p=11443633&postcount=59")    #[**60**]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60") 
This may relate to most of next generation devices it may help you get connected (but I never say die) as each device is different ,
the below is left for historical purposes , if asking why : then a udev rule may be required to bring up the net interface , so worth reading. again (I never say die) if read through most of this thread , had promise script to identify some modem ports
most of this was in place until these device came up,, the script will , hopefully identify most devices , suggest which switching methods can be use + the udev rules , + check which port could be the modem  + a suggested udev rule to bring the interface up
as to the historical purpose of leaving the below , look near end of the thread where found the UDEV RULES to bring the net interface up : as said the script is nearly done, and will post asp : it's been a busy year , well thats my excuse , but true , again never say die :: First part now at #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61") 

**Have new Huawie device** then look towards** Huawie Mobile Partner **, most Patches and Rules + Drivers are included: RE: POST #60 , link is above , don't forget to read further down this post RE; supported devices. And don't forget sakis3g , if you have not read **"the files" how to disable or as it is put "make the device available to third party"** and your stuck because modem manager can,t see the device, sakis3g should work. till you get sorted. OH and one last thing Check the** Sim Card** is inserted the **Right way**. had seen a few posts , Where Network Manager failed to **connect **or shows** offline **,, ???  **SEE POST**               #[**64**]("http://ubuntuforums.org/showpost.php?p=11709821&postcount=64") ** FIRST BEFORE COMMITTING**

alexfish
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[FONT=Verdana][SIZE=2][B] some require specific dialing methods, related <cid> dialing and cdc_ether interfaces + devices with multiple usb ID's
as an insight can look at these two posts [/B][/SIZE][/FONT]
#**[69]("http://ubuntuforums.org/showpost.php?p=10422455&postcount=69")**
 #**[73]("http://ubuntuforums.org/showpost.php?p=10425431&postcount=73")**
**update (24 feb 2011)as to some progress**             #[**82**]("http://ubuntuforums.org/showpost.php?p=10451640&postcount=82")   ::: #[**87**]("http://ubuntuforums.org/showpost.php?p=10490373&postcount=87")

and finaly  **[SOLVED]** [**Vodafone USB (K 3805-z)**]("http://ubuntuforums.org/showthread.php?t=1669429") {may also apply to Vodafone USB (K 3806-z)not tested (best go to last page)

**Re: NEW verizon lg vl600 4g(lte) aircard not working** can have a look at this post (patch available . if the .py files have[COLOR=Blue]#! /usr/bin/python3[/COLOR] , try edit to  #! /usr/bin/python ) #**[19]("http://ubuntuforums.org/showpost.php?p=10604695&postcount=19")** : patch level .38 : patch level .35 #[**23**]("http://ubuntuforums.org/showpost.php?p=10617499&postcount=23") >>>**read both.**
 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
(update 6 feb 2011 , you may find that some of these devices have 2 modem ports , this for one makes life difficult , which one to choose?
........ also of note the device nodes tty* may be different depending on it's state at boot time )
 [FONT=Verdana][SIZE=2][B]Best advice I can give at present :
If Network Manager is failing to connect using APN 
1.
use <cid> method of dialing , + omit the APN  ,
2. 
refrain from persistent attempts at dialing APN,s , it could have adverse affect on the sim card (take this as literal)
3.
list the device ports with the "ls -al /dev/serial/by-id" , then check each port for a connect message , using the <cid> method of dialing
have copied a later post concerning Meerkat to post #2, an will be updating , as and when info becomes available
[/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]**4. there is a sample output of the usb-devices command at the foot of this post** **.REF:  INFO**  possible **4g  LTE DEVICE**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]**5.** **there appears  be on going discussions at usb_modeswitch forum** regarding 4g LTE devices , suggest users to get involved [ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]**6. update the usb id's**[/SIZE][/FONT]
```
sudo /usr/sbin/update-usbids
```[FONT=Verdana][SIZE=2][B]Check to see if recognized 
[/B][/SIZE][/FONT]```
nm-tool 
```Can use this at any time to see status of NM network

can also use nmcli : may be built in , try the command 
```
nmcli
```for reference :[http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html)
**Link indicates :Where to report NM bugs> The Preferred Method of reporting : IE the SOURCE**
if not part of the distro: 
**can  suggest installing:command-line client for network manager : cnetworkmanager**


[FONT=Verdana][SIZE=2]**For link to Compatible devices **[/SIZE][/FONT]#[**Compatable Devices post #46**]("http://ubuntuforums.org/showpost.php?p=10367401&postcount=46")[B] / looks if this info could be outdated. best reference , try
[http://en.wikipedia.org/wiki/NetworkManager#Mobile_broadband_configuration_assistant](http://en.wikipedia.org/wiki/NetworkManager#Mobile_broadband_configuration_assistant)

usb_modeswitch data

or if already have the device:
simply connect the device  then read through rest post #1 [/B]**and post #2 , see if it is recognized.**
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2][B]VMC and BMC connection manager {re vodafone mobile connect)
Check this site : [http://www.betavine.net/bvportal/resources/datacards/os/ubuntu ]("http://www.betavine.net/bvportal/resources/datacards/os/ubuntu")
If Software Manager installed. use the debian package , it may inform  problems with package , if advises not to install or prevents install : take heed
[/B] for VMC check this out [/SIZE][/FONT][Vodafone Mobile Connect Software]("http://www.pcurtis.com/ubuntu-mobile.htm#vmc") . with a reference to permissions
[FONT=Verdana][SIZE=2] if you are  experiencing [/SIZE][/FONT][FONT=Verdana][SIZE=2]connection problems , and the network manager is failing to recognize the device [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]compatible devices also check post[/SIZE][/FONT]  #[**55**]("http://ubuntuforums.org/showpost.php?p=11150436&postcount=55")[FONT=Verdana][SIZE=2].. A lot of users fail to read all documentation .. Finally :Always READ the info at the site before Commiting

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Natty users also check this post :**[/SIZE][/FONT]#[**54**]("http://ubuntuforums.org/showpost.php?p=11038037&postcount=54")

[FONT=Verdana][SIZE=2] prior to installing this software established a connection  with the methods listed below , other than Network Manager.>> 3g ... Suggest Sakis3g .. others PPP . wvdial...
take this as a must do if have devices not listed in the data-cards/index page , have tested this latest software , and constantly refuses or times out , on devices requiring simPIN
IE: it can't get the device to accept the PIN number , so advise disable the PIN function on the device , if a problem

**Laptops:** have tested numerous Laptops , where by the usb devices are not registering . Check the bios configurations as regards usb1 and usb2 settings,
these setting are important,as it will also affect the speed of the device (sometimes may also apply to older desktops).
if still a problem, then **suggest trying Sakis3g** to find the device and update the system, if successful, then should see the device in network manager
(date: June 6, 2011)



**Begin**[/SIZE][/FONT][FONT=Verdana][SIZE=2]:

[/SIZE][/FONT]  [FONT=Verdana][SIZE=2] Boot up the computer without the modem give time for the system to settle then connect the modem:Obvious if the modem is part of the system {you can't plug it in}
[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Natty users**[/SIZE][/FONT]: Connect device prior to booting , after boot, modem manager will take time to process the device, be patient
[FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][FONT=Verdana][SIZE=2]Click on the Network Manager you may see something like " Make Connection" , click on it and follow the Wizard

The Network Manager at default is in the Notification area ,Top Panel ,right hand side , or can call up the the connections from the Terminal
[/SIZE][/FONT]```
nm-connection-editor
```[FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]IF 3g Connection: Require correct APN and {username and password if required }relevant to Your Pay Plan Check with your ISP
Note: For New Devices Ask If the Device Dial Method is <CID>
[/B] 
Importance of User names and passwords .Generally these are used for CDMA connections if using CHAP ;.. 3g generally uses PAP {no username or password required}, the pppd Daemon usually negotiates this automatically,  as for 3g connections your service provider may at times want authorization using CHAP, hence sometimes you may experience problems getting connected because your configurations has no User name or Password ,try entering your user-name and password for your service provider,  the connections can be monitored in the system log viewer messages
Need to retrieve this info from the sms texts have a look at pos[/SIZE][/FONT][FONT=Verdana][SIZE=2]t #[27]("http://ubuntuforums.org/showpost.php?p=9607429&postcount=27")

[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]you may be able to find your service  providers APN from the terminals ,connect the modem

IF intending to Install Huawei Mobile Partner , then suggest getting the necessary info ( apn + {mcc and mnc numbers to look up the info in providers data base} )
prior to install , it will help with the configuration... had been doing script to automate this , but found glitch in (updated serviceproviders.2.dtd :re attlist ussd replacement code)
will post this asp, so keep a watch out :dated 22nd feb 2012

Also look through the "10-Huawei-datacard.rules" to see if your device is supported : if device not supported, read next paragraph (Script at Post) this will
help to add an unlisted device to the rules , but read and digest how the rules are related ; since there are patches to certain drivers , Hint:may be possible to
add devices other than Huawei. [COLOR=Blue]All the info and how-to already  posted at #59 #60 #61 #62, Read All Before Commiting , Post #60 relates to if Modem-Manager sees the Device using the "dbus" if so the Info may Help to configure Huawie Mobile Partner[/COLOR]

[/B] [/SIZE][/FONT][FONT=Verdana][SIZE=2]Open up first terminal to monitor the modem outputs :To find the ports** : read below** [/SIZE][/FONT][FONT=Verdana][SIZE=2]**{Example :**[/SIZE][/FONT][FONT=Verdana][SIZE=2] FINDING THE PORTS**} Also see post #2 **[/SIZE][/FONT][COLOR=Blue]**[COLOR=Black]UDEVADM:[/COLOR]**[/COLOR][FONT=Verdana][SIZE=2] or can try;
Script at POST [/SIZE][/FONT] #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61") , with arg tty , it will give all necessary info IE ; which could be the modem port,, if the response to AT command = OK and the STATUS lines have 1's in them may assume modem port, this is
helpful if the device endpoints = 2 , most modems have 3 so easy identified, this will show in the **udev** info displayed , **for user of 11.10 **, may have to install **tclsh** , there are links at same post of how to do this the easy way , for future , keep a copy on usb stick
[FONT=Verdana][SIZE=2] 
[/SIZE][/FONT][FONT=Verdana][SIZE=2] edit the **tty[COLOR=Blue]PORT[/COLOR]** to suit the modem 
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
```
[SIZE=2]tr -s "\n" < /dev/ttyUSB2[/SIZE]
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]open up a second terminal[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
```
[SIZE=2]echo -e "AT\r" > /dev/ttyUSB2[/SIZE]
```if response
> OK assume the device is responding

to find APN's on device
[/SIZE][/FONT]```
[SIZE=2]echo -e "AT+CGDCONT?\r" > /dev/ttyUSB2[/SIZE]
```[FONT=Verdana][SIZE=2]example response from the first terminal[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]> [FONT=Verdana][SIZE=2]+CGDCONT: 1,"IP","","0.0.0.0",0,0
+CGDCONT: 2,"IP","payandgo.o2.co.uk","0.0.0.0",0,0
+CGDCONT: 3,"IP","m-bb.o2.co.uk","0.0.0.0",0,0
+CGDCONT: 4,"IP",[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue]general.t-mobile.uk[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]","0.0.0.0",0,0 <======= This is mine [/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]can be use as reference for <cid> dialing. Note the Number after +CGDCONT:
to dial <cid> reference the APN to the Number

example: for APN [/SIZE][/FONT] [FONT=Verdana][SIZE=2][COLOR=Blue]general.t-mobile.uk[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2] and Network Manager (remember , reference this to APN of NM connection Manager)
dial code = *99***4#
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]other dialers = ATDT*99***4#

example:for payandgo.o2.co.uk and Network Manager (remember , reference this to APN of NM connection Manager)
dial code = *99***2#
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]other dialers = ATDT*99***2#
[/SIZE][/FONT] [FONT=Verdana][SIZE=2] 
Find  ISP or Operator
```
[SIZE=3]echo -e "AT+COPS?\r" > /dev/ttyUSB2[/SIZE]
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]this returned
[/SIZE][/FONT]> +COPS: [COLOR=#000080]0,0,"T-Mobile UK",2 [/COLOR]<=======This was mine /[FONT=Verdana][SIZE=2] also shows it is registered to the network. this may be " 0.0.0 " indicating the device is not registered ,safest way , register on windows machine , or 
"search net for a how to , Not for the novice"

Have been requested to re-instate these commands removed from other posts : may be of benefit if the modem has a sim card and connects through APN.

to find the mmc and mnc numbers
[/SIZE][/FONT]```
echo -e "AT+COPS=0,2\r" > /dev/ttyUSB2
```[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]```
echo -e "AT+COPS?\r" > /dev/ttyUSB2
```[FONT=Verdana][SIZE=2]Returns something like this
[/SIZE][/FONT]> +COPS: 0,[COLOR=Blue]2[/COLOR],"[COLOR=Blue]23430[/COLOR]",[COLOR=Blue]2[/COLOR][FONT=Verdana][SIZE=2] these numbers can be used to find apn ,user name , password from the
serviceproviders database , can copy and paste this in the browser
[/SIZE][/FONT]```
file:///usr/share/mobile-broadband-provider-info/serviceproviders.xml
```[FONT=Verdana][SIZE=2]
the mcc and mnc number is taken from "[COLOR=Blue]23430[/COLOR]" and splits into
mcc =[COLOR=Blue]234[/COLOR]
mnc =[COLOR=Blue]30

[COLOR=Black]To find service providers use the AT+COPS=? command[/COLOR]
[/COLOR][/SIZE][/FONT]```
AT+COPS=?
``` [SIZE=2]this will take time while it searches
be patient[/SIZE]
[SIZE=2]example reply[/SIZE]
```
+COPS: ([COLOR=Blue]2[/COLOR],"T-Mobile","T-Mobile","[COLOR=Blue]23430[/COLOR]",[COLOR=Blue]2[/COLOR]),(1,"T-Mobile","T-Mobile","23430",0),(3,"Vodafone UK","Vodafone UK","23415",2),(3,"Vodafone UK","Vodafone UK","23415",0),(3,"O2-UK","O2-UK","23410",0),(3,"Orange","Orange","23433",0),(1, "3","3","23420",2),(3,"Orange","Orange","23433",2) ,(3,"O2-UK","O2-UK","23410",2),
```[FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]have highlight the bits relative to the provider , also note the numbers before and after the sim identifier .
 
[/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2] [COLOR=Blue][COLOR=black]**Test **: **pin code or puk code** required
[/COLOR][/COLOR]```
[SIZE=3]echo -e "AT+CPIN?\r" > /dev/ttyUSB2[/SIZE]
```[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=black][B]example results:
[/B][/COLOR][/COLOR]> **AT+CPIN?**
+CPIN: READY ME......is not pending for any password
+CPIN: SIM PIN CHV1...is required
+CPIN: SIM PUK PUK1 ..is required
+CPIN: SIM PIN2 CHV2..is required
+CPIN: SIM PUK2 PUK2..is required
+CPIN: PH-SIM PIN SIM.lock (phone-to-SIM) is required
+CPIN: PH-NET PIN.....Network personnalisation is required
+CME ERROR: <err> SIM failure (13) absent (10) etc..[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=black].**important** :if wrong pin is used 3 times then you will be sim locked , IE. device not accessible , ensure correct PIN Number or PUK code:
best advice : disable the PIN and PUK code security : Try to do this By inserting sim in mobile phone

[/COLOR] [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Red]EXIT the terminals when trying the  connection with Network Manager[/COLOR][/SIZE][/FONT]
[FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black] 
There is a script called mm-test.py (python using dbus to communicate with modem-manager) it will do most of the above and more
can use wget from the terminal if have alternate method of connecting
**Note:** BCM and WADER-CORE  the dbus spec is different to the modem-manager : hence the script may fail . will have to adapt code in mm-test.py dbus spec see post [/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]**:**[/SIZE][/FONT]#[**54**]("http://ubuntuforums.org/showpost.php?p=11038037&postcount=54")

**TESTING MODEM-MANAGER:** need to get mm-test.py :: To do the test disable all networking on the Network Manager
```
wget http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py
```[FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]to call the script
[/COLOR][/COLOR][/SIZE][/FONT]```
python ./mm-test.py
```[FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]
or paste this in the browser
[/COLOR][/COLOR][/SIZE][/FONT]```
http://cgit.freedesktop.org/ModemManager/ModemManager/plain/test/mm-test.py
```[FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black] then use copy and paste or save as. (name the script "mm-test.py")
to test a device open up a terminal ,cd to the directory where the script resides then
[/COLOR][/COLOR][/SIZE][/FONT]```
python ./mm-test.py
```  [FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]To get this to work as it should can Look here [/COLOR][/COLOR][/SIZE][/FONT]: [http://ubuntuforums.org/showpost.php?p=11469183&postcount=9](http://ubuntuforums.org/showpost.php?p=11469183&postcount=9)

**for rest of functions (argv's)**
[FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]Please read the script, Have fun[/COLOR][/COLOR][/SIZE][/FONT]

[SIZE=2]**Have also Written Bash Script (using dbus-send and modem-manager) to do Similar **[/SIZE]: SEE : POST  #[**62**]("http://ubuntuforums.org/showpost.php?p=11585976&postcount=62") 
[FONT=Verdana][SIZE=2][COLOR=Blue][COLOR=Black]
[/COLOR][/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]Even if the device is  {[/SIZE][/FONT][FONT=Verdana][SIZE=2] **not **[/SIZE][/FONT][FONT=Verdana][SIZE=2]**recognised** or **problematic** } , continue to make a new connection by the selecting  VPN Connections  ,it will help with some of the details if an alternate method of dial up needs to be used.[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Network manager failed to connect : Double check the Information and read the above with reference to NEW DEVICES APPEARING 

Device is Recognized and have double checked the information try the below methods of dial up

Device not recognised in the Network Manager : follow the below .  [/SIZE][/FONT][FONT=Verdana][SIZE=2]Also Checkout Post  #[B][16]("http://ubuntuforums.org/showpost.php?p=9483244&postcount=16")
[/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]also look for in same post
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000][B]Modem-Modeswitch :
setting the udev rules.d[/B][/COLOR][/SIZE][/FONT] [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]    
[LIST]
[*][FONT=Verdana][SIZE=2]If     it is not recognised and an icon appears and the desktop try right     click with mouse and **"eject**" or **"safely remove**" the device then see if     will configure [/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]There is a difference between the  [/SIZE][/FONT][FONT=Verdana][SIZE=2]**"eject**" and **"safely remove**". so it is best to monitor the effect it has on your Modem and the Network Manager
[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**To help you to understand why some device are not recognised** on a Linux the system :**Read info** at the site relating to the **usb modeswitch**[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**For Sierra Wireless check **[http://sierrawireless.custhelp.com/](http://sierrawireless.custhelp.com/)[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]also  sierra wireless [http://ubuntuforums.org/showthread.php?t=1548595](http://ubuntuforums.org/showthread.php?t=1548595)[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]also see [http://ubuntuforums.org/showthread.php?t=1668918](http://ubuntuforums.org/showthread.php?t=1668918)
[/SIZE][/FONT]
[/LIST]
                                   
[LIST]
[*][FONT=Verdana][SIZE=2]**If nothing happens** , open     up  the  terminal and enter this command 
[/SIZE][/FONT]
[/LIST]

[FONT=Verdana][SIZE=2]**Example :**[/SIZE][/FONT][FONT=Verdana][SIZE=2] FINDING THE PORTS[/SIZE][/FONT]
[SIZE=2]this command may show the tty*port for the modem[/SIZE]
[SIZE=2]```
ls -al /dev/gsmmodem
```[/SIZE]
[SIZE=2]example reply
> lrwxrwxrwx 1 root root 7 2011-07-01 13:41 /dev/gsmmodem -> ttyUSB2[/SIZE]
[SIZE=2]or try[/SIZE]
  [FONT=Verdana][SIZE=2] ```
dmesg | grep -e "modem" -e "tty"
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]This will show if the modem has been identify and the lines { ttyx } and possible the driver
[/SIZE][/FONT]> [FONT=Verdana][SIZE=2][COLOR=#0000ff][ 0.000000] console [tty0] enabled
[ 0.262809] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=DarkGreen][ 0.263080] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[ 21.950573] USB Serial support registered for GSM modem (1-port)
[ 21.950756] option 1-10:1.0: GSM modem (1-port) converter detected
[ 21.950893] usb 1-10: GSM modem (1-port) converter now attached to [/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue]**[COLOR=Black]tty[/COLOR]USB0**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[ 21.950911] option 1-10:1.1: GSM modem (1-port) converter detected
[ 21.951003] usb 1-10: GSM modem (1-port) converter now attached to [/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue]**[COLOR=Black]tty[/COLOR]USB1**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[ 21.951025] option 1-10:1.3: GSM modem (1-port) converter detected
[ 21.951130] usb 1-10: GSM modem (1-port) converter now attached to [/SIZE][/FONT][FONT=Verdana][SIZE=2]**tty[COLOR=Blue]USB2[/COLOR]**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[ 21.951157] option: v0.7.2:USB Driver for GSM modems[/SIZE][/FONT][FONT=Verdana][SIZE=2]**F**[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]or serial legacy devices:
[/B][/SIZE][/FONT]> [FONT=Verdana][SIZE=2][17179575.588000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.588000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.592000] 00:07: tty[COLOR=Blue]S0[/COLOR] at I/O 0x3f8 (irq = 4) is a [COLOR=Black]16550A[/COLOR]
[17179575.592000] 00:08: tty[COLOR=Blue]S1[/COLOR] at I/O 0x2f8 (irq = 3) is a [COLOR=Black]16550A[/COLOR]
 [/SIZE][/FONT][FONT=Verdana][SIZE=2]If only shows the 2 lines highlighted in blue then there is a problem

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**If the the output looks similar to the above then the Problem is a configuration one /**[/SIZE][/FONT][FONT=Verdana][SIZE=2] make a note of the ttyx as this will help to configure PPP , wvdial or Gnome-ppp
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
One thing is for sure : [/SIZE][/FONT][FONT=Verdana][SIZE=2][B]if the modem is recognized then there is no reason a connection can't be made { other than no signal , poor quality reception(signal strength),network busy (you can,t get a slot)  < = > sometimes your operator may drop the connection if you are leaving your network connection unattended.}

[/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]**USB_MODESWITCH:**[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][COLOR=#000000]**Note that the debian package is not 100% compatible with recent Ubuntu version**[/COLOR][/SIZE][/FONT]
   
[LIST]
[*][FONT=Verdana][SIZE=2]For USB Devices ;If nothing     shows enter this command from the terminal[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2] ```
lsusb
```this will give the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ID's**[/SIZE][/FONT][FONT=Verdana][SIZE=2] of the device
Look to see if your device is listed in the latest [/SIZE][/FONT] [device_reference.txt]("http://www.draisberghof.de/usb_modeswitch/device_reference.txt")[FONT=Verdana][SIZE=2]

**Natty users :read this before committing **[/SIZE][/FONT]  #[**30**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")[FONT=Verdana][SIZE=2]  (**same rules now apply with Ubuntu 10.10**) : if in doubt **check the details in synaptic** (usb-modeswitch properties)
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Check :**
[/SIZE][/FONT]  
[LIST]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**DefaultVendor     = [COLOR=Blue]0xN[/COLOR]**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]     where n is the number in hex[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**DefaultProduct     = [COLOR=Blue]0xN[/COLOR]**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]     where n is the number in hex[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]If     the device is listed then there is a good chance it will work[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]use     a **computer** with **Internet** access for any downloads and     save to usb stick , also you will always have the necessary tools to     get connected ; if you are a novice use links to the **Debian sites     **as the files will self install when in **Ubuntu **[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]if     you install the latest package then the device should work without     any further configuration of the usb modeswitch[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**read     all** the info at the **Draisberghof.de site** thoroughly and     note any areas of **problems** and the **fixes** and the **links**[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000][B]modeswitch compilation errors RE libusb, possible lib has no link, read [http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=605](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=605)
[/B][/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**Note that the debian package is not 100% compatible with recent Ubuntu version**[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000][B]whilst at the site , note indicating , device can be broken if wrong msg content sent "for me , I would take it back for a refund"
[/B][/COLOR][/SIZE][/FONT]
[/LIST]
   
[LIST]
[*] [device_reference.txt]("http://www.draisberghof.de/usb_modeswitch/device_reference.txt")[FONT=Verdana][SIZE=2](formerly known as usb_modeswitch.conf. if recent version of Ubuntu , could be on system as tar file)[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)[/SIZE][/FONT]
[*]**[FONT=Verdana][SIZE=2]Ubuntu packages search[/SIZE][/FONT]**
[*]                                  [FONT=Verdana][SIZE=2][http://packages.ubuntu.com/](http://packages.ubuntu.com/)[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Dial up :Methods**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  
[LIST]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**Gnome     Network Manager **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]{     Should already be installed } Also has a list of predefined     connections[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**Gnomeppp**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]     this is a front end tool to wvdial so both need to be down loaded     {Also check post [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]            #[**6**]("http://ubuntuforums.org/showpost.php?p=9219104&postcount=6")[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000] by George Vita }[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**Sakis3g **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]     refer to the post[/COLOR] [/SIZE][/FONT]#5
[*][FONT=Verdana][SIZE=2][COLOR=#000000]**PPP**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]     { should already be installed. [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]**set     up**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]     use the terminal and enter the command : [/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]**sudo     pppconfig { Example at Post **[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]  #[**7**]("http://ubuntuforums.org/showpost.php?p=9223400&postcount=7")[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]**}**[/COLOR][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000]** Mozilla Firefox ,**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]**if     the browser is not working check the "Work Off line" is     unchecked**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][B][URL="http://kb.mozillazine.org/Toolkit.networkmanager.disable"]
[/URL][/B][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2]**Tip for the Mozzila Firefox fix ,After opening Firefox, try opening page "about:config"... Filter for "toolkit.networkmanager.disable"**[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][B]Change the line to ....." toolkit.networkmanager.disable;true "
[/B][/SIZE][/FONT]
[/LIST]
  [FONT=Verdana][SIZE=2][COLOR=#000000]**Downloads :**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  
[LIST]
[*]**[FONT=Verdana][SIZE=2][COLOR=#000000]Gnomeppp and wvdial search packages[/COLOR][/SIZE][/FONT]**
[*][FONT=Verdana][SIZE=2][http://packages.ubuntu.com/](http://packages.ubuntu.com/)[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][B]sakis3g 
[/B][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][COLOR=#000000] [http://www.sakis3g.org]("http://www.sakis3g.org/")[/COLOR][/SIZE][/FONT]
[/LIST]
    [FONT=Verdana][SIZE=2] 
**Network Manager:**
**ISP** failing to return the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS1**[/SIZE][/FONT][FONT=Verdana][SIZE=2] and [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS2**[/SIZE][/FONT][FONT=Verdana][SIZE=2] IE :the modem connects but the Browser and updates etc fail to connect

[/SIZE][/FONT][FONT=Verdana][SIZE=2] From the terminal try these[/SIZE][/FONT][FONT=Verdana][SIZE=2]
```
sudo gedit /etc/ppp/options
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Add this line and save:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
```
replacedefaultroute
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Or**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

Here I have change the IPCP configure-NAKs returned before starting , remove the # and set the number to 30 ( or any thing above the default value till there is a constant connection ) Tip try 30 then work down
[/SIZE][/FONT][FONT=Verdana][SIZE=2]```
sudo gedit /etc/ppp/options
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Place a # in front of the [COLOR=Blue]replacedefaultroute[/COLOR] so it looks like **[/SIZE][/FONT][FONT=Verdana][SIZE=2]
```
# replacedefaultroute
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Then look for the lines :**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
> # Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
# ipcp-max-failure <n>[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]edit to look like :
[/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]```
# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).

ipcp-max-failure 30
```[/SIZE][/FONT] [FONT=Verdana][SIZE=2]Hopefully I can now leave the NM IPv4 settings to Automatic (PPP) instead of Setting the NM to IPv4 settings to Automatic (PPP) address only and having to enter the numerical addresses in the DNS servers text box.

the [/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=Blue]**replacedefaultroute**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2] has failed a few times after a fresh boot , but has proved quite successful.

Alternatively you can use the Network Manager to use the address of your [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ISP **[/SIZE][/FONT][FONT=Verdana][SIZE=2]

get the Numerical address or addresses from your [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ISP**[/SIZE][/FONT][FONT=Verdana][SIZE=2] commonly known as [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS1**[/SIZE][/FONT][FONT=Verdana][SIZE=2] and [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS2**[/SIZE][/FONT][FONT=Verdana][SIZE=2], or DNS1 and DNS2.

Open up the connection via the Network Manager . Select Mobile Broadband . Select Edit Connection .Select Ipv4 settings select the Automatic(PPP) address only then enter the addresses of your [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ISP**[/SIZE][/FONT][FONT=Verdana][SIZE=2] in the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**DNS servers box**[/SIZE][/FONT][FONT=Verdana][SIZE=2] separated by a &#8220; [/SIZE][/FONT][FONT=Verdana][SIZE=2]**, **[/SIZE][/FONT][FONT=Verdana][SIZE=2]&#8220; comma without the quotes so it will look something like
```
149.254.201.126,149.254.192.126
```[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]Making back up files:

[/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]Networking and wireless software "configuration files" use the home directory and the "/etc/" directory for configurations, so I recommend backing up any file you are attempting to edit

[/SIZE][/FONT][FONT=Verdana][SIZE=2]Making back up files:
[/SIZE][/FONT][FONT=Verdana][SIZE=2]> sudo cp "file path"/"file path_bak"[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]Example:
[/B][/SIZE][/FONT]```
[FONT=Verdana][SIZE=2][COLOR=Black]sudo cp /etc/ppp/options /etc/ppp/options_bak[/COLOR][/SIZE][/FONT]
```[FONT=Verdana][SIZE=2]
for files which would be stored in the home directory I recommend backing up the actual "home" directory it's self. ,know a few people that deleted all the contents ,even deleted the home directory to make a new one ? .  If you have plenty of storage , backup the whole of the "/etc/" as well . if your asking why " **Some hidden** " . { also advise backing up if upgrading to different versions of Ubuntu}[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]      
[LIST]
[*]**[FONT=Verdana][COLOR=Black][SIZE=2]Every     Thing I have tried Failed[/SIZE][/COLOR][/FONT]**[FONT=Verdana][SIZE=2]: Search the     forums with your Model or start new Thread at[/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][Networking     & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")[/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2][B]check to see if usb-devices are on system
[/B]```
which usb-devices
```if on system :reply[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]=
[/SIZE][/FONT]>  [FONT=Verdana][SIZE=2][COLOR=Blue]/usr/bin/usb-devices[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2]it is installed

to find details of device[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
```
usb-devices
```[/SIZE][/FONT]    [FONT=Verdana][SIZE=2]**Notes :**
[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Modem Port recognition :**[/SIZE][/FONT]                                   [FONT=Verdana][SIZE=2]

**Gobi chipset problems**   [/SIZE][/FONT][FONT=Verdana][SIZE=2]... {**Maverick Meerkat** should now have the  **gobi-loader** in the repo's** Check Synaptic Package Manager** }
  [/SIZE][/FONT][FONT=Verdana][SIZE=2]also look here
[http://ubuntuforums.org/showthread.php?t=1507954](http://ubuntuforums.org/showthread.php?t=1507954)

**Ubuntu 10.04**[/SIZE][/FONT][FONT=Verdana][SIZE=2]  :Some devices may load and configure on boot  and not visible from the desk top
 also not available from the network manager as the pppd has self initiated . Check this out from the  log file viewer , also see if you can browse. I suggest installing netspeed as any connection will show in the netspeed.  reason { reports of devices previously available before upgrading to 10.04 }{added 6 june 2010}

  Connecting  the modem on the main hub {on the motherboard back plane}can lead to device recognition errors[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]
  Noticeable with USB harddrives , boot from USB stick ,  Keyboard or Mouse 
  To check for conflicts use the  &#8220;  lsusb -t  and lsusb &#8211;v &#8220; command  and monitor the outputs

**Modem Firmware upgrades: **[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]
  Some Manufactures and Providers are providing firmware updates to meet requirements of win7 , if you accept these updates be prepared for some devices to be no longer recognized in Linux . [/SIZE][/FONT] [FONT=Verdana][SIZE=2]Also checkout Posts[/SIZE][/FONT][FONT=Verdana][SIZE=2]#29 and 30[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2] 
I can only suggest this , if the device is working , leave as is , or ask the question " If  I upgrade the firmware , will it still work with linux &#8220;.[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]

**Some devices need time to settle**[/SIZE][/FONT][FONT=Verdana][SIZE=2] **:** if there is sporadic identification of the device or the ports been registered this may more notable in 10.04 , try connecting the device after boot
**or**[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]
Add in [COLOR=Blue]/etc/modprobe.conf[/COLOR] a delay for the usb-storage[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]```
sudo gedit /etc/modprobe.conf 
```[/SIZE][/FONT][FONT=Verdana][SIZE=2]add the following line 
```
options usb-storage delay_use=1
```[/SIZE][/FONT][FONT=Verdana][SIZE=2] (or 10, or other) 5 is a good bench mark To start[/SIZE][/FONT] [FONT=Verdana][SIZE=2]

**Save and exit**[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
[/SIZE][/FONT] [FONT=Verdana][SIZE=2]
here is an interesting Solve for a Toshiba with built in modem [/SIZE][/FONT][FONT=Verdana][SIZE=2]"Apparently the[/SIZE][/FONT][FONT=Verdana][SIZE=2]** 3g modem Radio is by default set to OFF**[/SIZE][/FONT][FONT=Verdana][SIZE=2] ."[/SIZE][/FONT][FONT=Verdana][SIZE=2] [SOLVED] [Toshiba built-in 3g Modem (F3507g)]("http://ubuntuforums.org/showthread.php?t=1477911")

[/SIZE][/FONT][FONT=Verdana][SIZE=2][COLOR=#000000]**A site worth reading**[/COLOR][/SIZE][/FONT][FONT=Verdana][SIZE=2][[COLOR=#000000]............http://www.pcurtis.com/ubuntu-mobile.htm[/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm")[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT] [FONT=Verdana][SIZE=2] **Stubborn devices; look at the screen shots**[/SIZE][/FONT]                                   [FONT=Verdana][SIZE=2]
This device was ejected from the desktop it sometimes was not recognized as a modem , but had habit of remounting  [/SIZE][/FONT]   [FONT=Verdana][SIZE=2]
to find were these devices goto  , open up the  disk utility  in the system administration  [/SIZE][/FONT]   [FONT=Verdana][SIZE=2]

**REF:  INFO**  possible **4g LTE DEVICE . **manufacture data suppressed 
[/SIZE][/FONT]> I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 5 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 7 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=(none)
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)[FONT=Verdana][SIZE=2] 
the screen shots should be self explanatory:  try using eject or  safely remove  , as mentioned near top of post . " There is a difference between Ejecting the device and Safely removing ", Monitor the results

[/SIZE][/FONT]

---

### Post by alexfish on 2010-04-30
**Reference Ubuntu Maverick Meerkat :**
[SIZE=2]**READ ALL BEFORE COMMITTING**
[/SIZE]**ALL ARE EXAMPLES : EDIT THE DETAILS ACCORDING TO YOUR DEVICE ID's (you have been advised)**

**Reference Ubuntu Maverick Meerkat : note usb_modeswitch and udev rules , not same as previous versions of Ubuntu,see  **[FONT=Verdana][SIZE=2]**USB_MODESWITCH: POST #1**[/SIZE][/FONT]
[SIZE=2] AT COMMANDS PDF REFERENCE :REMAINS see foot of post

[/SIZE]**Huawie devices and other's .:Option driver not loading**: Note the option driver is normally used with 3g devices
**ZTE Devices not Switching  **See foot of page:same type of rule may apply for other new devices not recognized by udev or the kernel

to check . open up a terminal , enter the following code
```
usb-devices
```the output will look similar to 
> T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #[COLOR=Blue]EPs= 3[/COLOR] Cls=ff(vend.) Sub=ff Prot=ff[COLOR=Blue] Driver=(none)[/COLOR]
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Blue]Driver=(none)[/COLOR]
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=[COLOR=Blue]ff Driver=(none)[/COLOR]
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage(each device may show different parts)
also note " [COLOR=Blue]EPs= 3 [/COLOR]" this usually indicates the modem

Notice the lines where it shows [COLOR=Blue]Driver=(none)[/COLOR]

From the terminal enter the following code,to load the driver module 
```
sudo modprobe option
```enter your system password

then repeat the command "[COLOR=Blue]usb-devices[/COLOR]"

you should now see
> T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Blue]Driver=option[/COLOR]
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Blue]Driver=option[/COLOR]
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff [COLOR=Blue]Driver=option[/COLOR]
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storagedevice should now be ready

as a temporary fix (applies to recent Ubuntu versions with usb_modeswitch) 
Can try this
```
sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
```scroll down to the line which shows the id's of the device

EXAMPLE:
> # Huawei E169
[COLOR=Blue]ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"[/COLOR]disable the line with a** #** . Add a line so it looks like the below . also double check the ID's prior to saving
```
# Huawei E169
#ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="/sbin/modprobe  option"
```save the file : unplug the device then reconnect : note  changes by using the "usb-devices" command

If the mode-switching has been disabled (**device not switching**) remove the "**#**": note changes by using the "usb-devices" command
**If the above has no effect reverse the changes **: 

[B]once done: exit gedit

NOTE : after updating the system : check and reverse the changes : see what happens[/B]

[B] ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

if the dialout method requires ID  the modem port (recommend using Sakis3g as a tool (use more options menu) to update system , although it can't dial true CDMA: IE dial command #777)
also may save having to write new rules esp if new device + details not in any of the udev rules  
[/B]```
usb-devices
```this should give output similar to
> T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=02 Dev#= 13 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I: [COLOR=Blue] If#= 0 Alt= 0 #[/COLOR][COLOR=Blue]EPs= 3[/COLOR] Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storageNote the[COLOR=Blue][COLOR=Black] "[/COLOR] If#= 0 Alt= 0 #[/COLOR][COLOR=Blue]EPs= 3[/COLOR][COLOR=Black] "[/COLOR] : the part with EPs= 3 usually indicates the modem
```
ls -al /dev/serial/by-id/usb*
```this should give output similar to
> /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-[COLOR=Blue]if00-port0 -> ../../ttyUSB0[/COLOR]
/dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
/dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2Note the line with the [COLOR=Blue]if00-port0 -> ../../ttyUSB0[/COLOR]

here are the  two important lines
> **I: [COLOR=Blue] If#= 0 Alt= 0 #[/COLOR][COLOR=Blue]EPs= 3[/COLOR] Cls=ff(vend.) Sub=ff Prot=ff Driver=option**

**/dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-[COLOR=Blue]if00-port0 -> ../../ttyUSB0[/COLOR]**read again from " [B]if the dialout method requires ID  the modem port"
[/B]Identify the
>  [COLOR=Black]"[/COLOR]**[COLOR=Blue] If[/COLOR]****[COLOR=Blue]**[/COLOR]** and  **[COLOR=Blue]EPs= 3[/COLOR]**[COLOR=Black] "[/COLOR] This device indicates the modem is on** [COLOR=Blue]ttyUSB0[/COLOR]**
Example: for wvdial 
> modem = /dev/ttyUSB0[COLOR=Blue] 

**[COLOR=Black]UDEVADM:[/COLOR]**
[COLOR=Black]**Note: udev rules does not allocate tty* as constant always check tty* : always check with "[COLOR=Blue]ls -al /dev/serial/by-id[/COLOR]"  or "**[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]**[COLOR=Blue]ls -al /dev/serial/by-path[/COLOR]"**[/COLOR][/COLOR]
[COLOR=Blue][COLOR=Black][B]Hence dialers like wvdial and ppp/chat with the tty* set as constant , may fail to identify the correct port , if the udev allocates a different device node

For info retrieval about devices suggest reading  udevadm man pages 
[/B][/COLOR][/COLOR]```
man udevadm
```[COLOR=Blue]
[B][COLOR=Black]Example: redirect outputs to home directory /udevinf
dump all .. note this device does not list [/COLOR][/B][/COLOR][COLOR=Blue]**[COLOR=Black] as a modem [/COLOR]**[/COLOR][COLOR=Blue][B][COLOR=Black]in Hal properties, listed by  " lshal " command
[/COLOR][/B][/COLOR]```
udevadm info --export-db > `pwd`/udevinfo
```open the file with gedit look for lines similar to
> P: /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.3/ttyUSB2/tty/ttyUSB2
N: [COLOR=Blue]ttyUSB2[/COLOR]
S: [COLOR=Blue]gsmmodem[/COLOR]
S: char/188:2[COLOR=Blue][B][COLOR=Black] 

However: this is where a data base can give the wrong info / if a device is incorrectly switched (usually by manually ejecting or safely removing the device)
hence reason for two methods of detecting the correct port / also makes twice as hard if the device only reveals Eps=2 /even harder if a newer devices with 2 modem ports
 can also be explained by reading post [/COLOR][/B][/COLOR]#[**16**]("http://ubuntuforums.org/showpost.php?p=9483244&postcount=16")
the original fix script has been removed , but will update ASP to include devices which reveal only 2 Eps: ** See Pos**t #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61")
[COLOR=Blue] [COLOR=Black]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[/COLOR][B][COLOR=Black]ZTE DEVICES NOT SWITCHING: Also may apply to other devices 

to find state of device : from the terminal
[/COLOR][/B][/COLOR]```
usb-devices
```[COLOR=Blue][COLOR=Black]example reply
[/COLOR][/COLOR]> T: Bus=01 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#= 5 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=[COLOR=Blue]19d2[/COLOR] ProdID=[COLOR=Blue]2000[/COLOR] Rev=00.00
S: Manufacturer=ZTE, Incorporated
S: Product=ZTE CDMA Technologies MSM
C: #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=05 Prot=50 Driver=[COLOR=Blue]usb-storage[/COLOR][COLOR=Blue][COLOR=Black]to fix try
[/COLOR][/COLOR]```
sudo gedit /etc/udev/rules.d/zte_eject.rules
```[COLOR=Blue][COLOR=Black]add this line edit the device ID's according to the device
[/COLOR][/COLOR]```
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```[COLOR=Blue][COLOR=Black]save exit , reboot with the device connected or can try udevadm to reload the rule
[/COLOR][/COLOR]```
udevadm control --reload-rules
```**[COLOR=Blue][COLOR=Black]Note any change with "lsusb" command[/COLOR][/COLOR]**
  [SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Note: if running udevadm test ..../*/* : and Debug info , indicates the use of SYSFS, then Change the rules accordingly 
add_rule: SYSFS{}= will be removed in a future udev version, please use ATTR{}= to match the event device, or ATTRS{}= to match a parent device, in /etc/udev/rules.d/*
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Some devices may not be recognized by the kernel modules(device recognition is usually built in)
so it is advantages to use a udev rule to use the generic usbserial driver (not always recommended)
but will suffice until  the modules get updated
note :if the device is getting switched by usb_modeswitch , then it may have been registered  to use the option module
this can be monitored by rebooting the system after modeswitching , long winded, but seems to work.  can check with udevadm test.

example of udevadm test .../*/* : locate the file to which part of the device resides ( as mentioned earlier , one reason to ensure the driver is loading , can use [/COLOR][/FONT][/B][/COLOR][/SIZE]"40-usb_modeswitch.rules)
```
udevadm test /sys/bus/usb/devices/1-3:1.0
```[SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black]this is a part of the output which indicates the usb_modeswitch binding the driver
[/COLOR][/FONT][/B][/COLOR][/SIZE]> udevadm_test: run: 'usb_modeswitch --driver-bind /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3:1.0   19d2/31/0'
udevadm_test: run: 'socket:@/org/freedesktop/hal/udev_event'[SIZE=2][COLOR=Red]**[FONT=Times New Roman, serif][COLOR=black]if driver not loaded possible , try reloading the rules with [/COLOR][/FONT]**[/COLOR][/SIZE]"udevadm control --reload-rules" command ,
see what happens
[SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black] 
example udev rule to load the generic usbserial driver (remember the device has to be in the switched mode : + edit the [COLOR=Blue]ID's[/COLOR] accoring to the device. )
[/COLOR][/FONT][/B][/COLOR][/SIZE]```
sudo gedit /etc/udev/rules.d/usbserial.rules
```[SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black]enter 
[/COLOR][/FONT][/B][/COLOR][/SIZE]```
ATTRS{idVendor}=="[COLOR=Blue]12d1[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]1001[/COLOR]", RUN+="/sbin/modprobe usbserial vendor=[COLOR=Blue]0x12d1[/COLOR] product=[COLOR=Blue]0x1001[/COLOR]"
```[SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black]save and exit

Rules: Renaming /dev/tty* : [/COLOR][/FONT][/B][/COLOR][/SIZE][SIZE=2][COLOR=Red]**[FONT=Times New Roman, serif][COLOR=black]This  type of renaming convention can make life easier for the likes of  wvdial, yet difficult for network manager , be careful as to its usage[/COLOR][/FONT]**[/COLOR][/SIZE]
[SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black] 
[/COLOR][/FONT][/B][FONT=Times New Roman, serif][COLOR=black]here is an example of renaming the dev nodes : from previous info determine the functions of
ATTRS{bInterfaceNumber}=="**" and the ATTRS{bInterfaceProtocol}=="**" then make the rule in the /etc/udev/rules.d[/COLOR][/FONT][B][FONT=Times New Roman, serif][COLOR=black]

example:[/COLOR][/FONT][/B][FONT=Times New Roman, serif][COLOR=black]here the modem port is at kernel ttyUSB0 : bInterfaceNumber 00 : [COLOR=Blue]**renamed to /dev/Huawei1_modem**[/COLOR] (remember to edit the device[COLOR=Blue] ID's[/COLOR] according to the device)[/COLOR][/FONT][B][FONT=Times New Roman, serif][COLOR=black]
[/COLOR][/FONT][/B][/COLOR][/SIZE]```
sudo gedit /etc/udev/rules.d/huawei1Nodes.rules
```[SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black]The rules
 [/COLOR][/FONT][/B][/COLOR][/SIZE]```
SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:[COLOR=Blue]v12D1p1001[/COLOR]*", KERNEL=="ttyUSB*", ATTRS{bInterfaceNumber}=="00", ATTRS{bInterfaceProtocol}=="ff", NAME="Huawei1_modem"
 SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:[COLOR=Blue]v12D1p1001*[/COLOR]", KERNEL=="ttyUSB*", ATTRS{bInterfaceNumber}=="01", ATTRS{bInterfaceProtocol}=="ff", NAME="Huawei1_ctrl"
 SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:[COLOR=Blue]v12D1p1001*[/COLOR]", KERNEL=="ttyUSB*", ATTRS{bInterfaceNumber}=="02", ATTRS{bInterfaceProtocol}=="ff", NAME="Huawei1_null"
```[SIZE=2][COLOR=Red][FONT=Times New Roman, serif][COLOR=black]note the changes with the "ls -al /dev/serial/by-id" command[/COLOR][/FONT][B][FONT=Times New Roman, serif][COLOR=black]
[/COLOR][/FONT][/B][/COLOR][/SIZE]```
ls -al /dev/serial/by-id
```[SIZE=2][COLOR=Red][B][FONT=Times New Roman, serif][COLOR=black]This type of renaming convention can make life easier for the likes of wvdial, yet difficult for network manager , be careful as to its usage
[/COLOR][/FONT][/B][FONT=Times New Roman, serif][COLOR=black]As mentioned earlier some devices can be[/COLOR][/FONT]**[FONT=Times New Roman, serif][COLOR=black] incorrectly switched [/COLOR][/FONT]**[FONT=Times New Roman, serif][COLOR=black]and[/COLOR][/FONT]**[FONT=Times New Roman, serif][COLOR=black] tty* can be of different Numbers , [/COLOR][/FONT]**[FONT=Times New Roman, serif][COLOR=black]if it is known That the modem part of the Device rule "bNumEndpoints=03,
then a udevrule can be used to good effect , see what I have done below with one such device, Note the difference in the rules, part of the old rules are disabled**(this is a must do**)
 [/COLOR][/FONT][/COLOR][/SIZE]```
SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:[COLOR=Blue]v12D1p1001*[/COLOR]", KERNEL=="ttyUSB*", ATTRS{bNumEndpoints}=="03", ATTRS{bInterfaceProtocol}=="ff", NAME="Huawei1_modem"
# SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:[COLOR=Blue]v12D1p1001*[/COLOR]", KERNEL=="ttyUSB*", ATTRS{bInterfaceNumber}=="01", ATTRS{bInterfaceProtocol}=="ff", NAME="Huawei1_aux"
# SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:[COLOR=Blue]v12D1p1001*[/COLOR]", KERNEL=="ttyUSB*", ATTRS{bInterfaceNumber}=="02", ATTRS{bInterfaceProtocol}=="ff", NAME="Huawei1_null"
```[SIZE=2][COLOR=Red][FONT=Times New Roman, serif][COLOR=black]

[/COLOR][/FONT][B][FONT=Times New Roman, serif][COLOR=black]
Note: at kernel level the tty* remain the same
[/COLOR][/FONT][/B][FONT=Times New Roman, serif][COLOR=black]**~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~**
**Advisory Note:**
Bugs should now be reported to the source . IE : if it were a usb_modeswitch bug, or OOps , then report to usb_modeswitch
**~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~**
[/COLOR][/FONT][B][FONT=Times New Roman, serif][COLOR=black] 

[/COLOR][/FONT][/B][/COLOR][/SIZE][SIZE=2]**Reference Guide **
**Products: MTSMC-Cxx, MTMMC-Cxx, MTCBA-Cxx **[/SIZE]  [SIZE=2]
**PN S000294D, Revision D **[/SIZE]  [SIZE=2]
[B]Multi-Tech Systems, Inc.

[/B][B]AT Commands for CDMA Wireless Modems 

[/B]**Including ,Reference to CDMA : Qualcomm ,Verizon**  [/SIZE][SIZE=2]® and **Sprint**®

**Qualcomm , Verizon**   [/SIZE][SIZE=2]®** and Sprint**®** ;  AT commands: read **[/SIZE] [SIZE=2]

Chapter 19 - Qualcomm Defined AT Commands for CDMA Operation[/SIZE]  [SIZE=2]
Chapter 22 - Verizon® Specific AT Commands
Chapter 23 - Sprint® Specific AT Commands

**Warning :**   [/SIZE][SIZE=2] the below file is in pdf format :clicking on the link to will automatically download the file

**[*AT Commands For CDMA* Wireless *Modems* Reference Guide]("http://igor.chudov.com/manuals/AT_Commands-For-CDMA-Modems-Incl_Qualcomm_U300.pdf")**[/SIZE]   [SIZE=2]

**VIEW ON LINE :AT COMMANDS**[/SIZE] [SIZE=2]3g and cdma/ originating link is for cdma /
[http://www.scribd.com/doc/41616367/CDMA-at-Commands](http://www.scribd.com/doc/41616367/CDMA-at-Commands)[/SIZE] [SIZE=2]
this site will list most known listed providers and or specific AT commands[/SIZE][SIZE=2]
including ZTE Corporation&#8217;s ME3000 Module/MG3006&#12289;MG3030&#12289;MG3036&#12289;MG3082&#12289;MG3088
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Sierra Wireless AT commands**[/SIZE]    [SIZE=2]

[http://www.sierrawireless.com/resources/documents/support/2130617_Supported_AT_Command_Reference-v2.4.pdf](http://www.sierrawireless.com/resources/documents/support/2130617_Supported_AT_Command_Reference-v2.4.pdf)[/SIZE]  [SIZE=2]

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**ZTE AT commands**  [/SIZE][SIZE=2] clicking on the link to will automatically download the file

                                  ZTE AT Commands [/SIZE] [SIZE=2][GSM/GPRS Module AT Command Mannual]("http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CBkQFjAB&url=http%3A%2F%2Fdownload.maritex.com.pl%2Fpdfs%2Fwi%2FAT%2520ZTE.pdf&rct=j&q=zte%20at%20commands&ei=MrZBTPXzHdD-4AaSwdHEDg&usg=AFQjCNGJvqV6_UzK3IPYq_S7yf0YAp8GOg")[/SIZE]

---

### Post by dino99 on 2010-04-30
nice job, thanks
bookmarked

---

### Post by alexfish on 2010-04-30
**[FONT=Times New Roman, serif][SIZE=3] Network monitoring and SMS Text services[/SIZE][/FONT]**
 
 [FONT=Times New Roman, serif][SIZE=3]**netspeed** :[/SIZE][/FONT]

 [FONT=Times New Roman, serif][SIZE=3]for monitoring net speed and will also confirm you have a connection ,handy if your process is running in the background and have no visual means that the service is running[/SIZE][/FONT] Eg{ PPP }
 [FONT=Times New Roman, serif][SIZE=3]
**pppstatus** :[/SIZE][/FONT]
 
 [FONT=Times New Roman, serif][SIZE=3]usage same as above + logging cost etc ; look [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]at the config files[/SIZE][/FONT]

 [FONT=Times New Roman, serif][SIZE=3]use from the  terminal  

[/SIZE][/FONT]```
pppstatus
```

**Still see posts on Can't monitor costs , emails etc**
try editing the pppstatus files
```
sudo gedit /etc/pppstatus/costs
```
```
sudo gedit /etc/pppstatus/pppstatus.cfg
```to get the pppstatus to run on boot look at **/etc/pppstatus/no_pppstatus_on_boot**
```
cat /etc/pppstatus/no_pppstatus_on_boot
```

[FONT=Times New Roman, serif][SIZE=3]**Wammu** :

SMS texts see screen shot : If you use the Network Manager for Your connection Ensure the Service is  "Available to All Users[/SIZE][/FONT]" ;[SIZE=2] [SIZE=3][FONT=Times New Roman]This will allow you to connect whilst using the Network Manager if the dongle has the facility[/FONT][/SIZE][/SIZE]

May not work if connect to net Ubuntu Meerkat
also may have to kill modem-manager
```
sudo killall modem-manager
```Suggest alternate method of connection for the network that only locks  one port
 
 [FONT=Times New Roman, serif][SIZE=3]
[/SIZE][/FONT]

---

### Post by alexfish on 2010-04-30
[SIZE=2]**Sakis3g :**[/SIZE][SIZE=2]
[/SIZE][SIZE=2]Advantages of sakis3g click on the &#8220;Sakis3G script is all about&#8221;[/SIZE]
[SIZE=2]**Getting started **[/SIZE]**:**

[LIST]
[*]Read what [Sakis3G script is all about]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_script").
[*][Installation guide]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation").
[*]Locate [user interface]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_UI") best fitting your environment, or explore its [command line]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_invocation") powers.
[/LIST]
[SIZE=2]**Getting support **[/SIZE]:


[LIST]
[*]Check if your [operator]("http://wiki.sakis3g.org/wiki/index.php?title=Operator") is found within [list of known operators]("http://wiki.sakis3g.org/wiki/index.php?title=Known_operators"), or [information you need to collect]("http://wiki.sakis3g.org/wiki/index.php?title=APN") if it is not.
[*]Learn how to [receive support]("http://wiki.sakis3g.org/wiki/index.php?title=Category:Support").
[/LIST]
[SIZE=2]**Read more **[/SIZE]:


[LIST]
[*]Read [Sakis3G manual]("http://wiki.sakis3g.org/wiki/index.php?title=Category:Manual").
[*]Check out [usage guides]("http://wiki.sakis3g.org/wiki/index.php?title=Category:Usage_guides").
[*]Read all about [dependencies and requirements]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_dependencies").
[*]How to [recompile it]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_compilation") if necessary.
[*]Learn how to [configure it]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_configuration").
[*][Frequently Asked Questions]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_faq").
[/LIST]
[http://wiki.sakis3g.org/wiki/index.php?title=Main_Page](http://wiki.sakis3g.org/wiki/index.php?title=Main_Page)

**Forum:**
[http://forum.sakis3g.org/smf/index.php](http://forum.sakis3g.org/smf/index.php)


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ ~~~~~~~~~~~~~~~~~~~
[SIZE=2]**How to install latest version** in **Ubuntu**: . Possibly **Sakis3g **0.2.0e[/SIZE] . 
now includes usb_modeswitch " Version 1.1.3 (C) Josua Dietze 2010"(should not affect other installed versions.[Tested with Ubuntu Meerkat])
[SIZE=2]**From the terminal:**[/SIZE]
```
sudo bash
```[SIZE=2]
[/SIZE]```
cd /usr/bin 
```[SIZE=2]step3: **NOTE:**the below is direct link ,clicking on the link,sets auto download, handy if need to download on usb stick
[/SIZE]```
wget "[http://www.sakis3g.org/versions/latest/i386/sakis3g.gz](http://www.sakis3g.org/versions/latest/i386/sakis3g.gz)"
```[SIZE=2]step4
[/SIZE]```
echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c 
```[SIZE=2]**You should see:**[/SIZE] [SIZE=2]sakis3g.gz: OK
[/SIZE]```
gunzip sakis3g.gz 
```[SIZE=2]
[/SIZE]```
chmod +x sakis3g
```then run sakis3g from the terminal
```
sakis3g
```if had no network connection / and download to usb stick , via other means , can try
open up nautilus in su mode
```
gksu nautilus
```locate the file , and copy to the /usr/bin, miss out step3

Only recommendation I could make here is this. if constant calls to sakis3g are made IE: from the terminal then ensure to killall after use
or make use of the option to create a shortcut / to the notification area.

**Stay connected:**
here is a small script to  keep connected called sakis-connect.
assuming the modem will connect with the command [/usr/bin/sakis3g silent "connect" APN=<yourAPN>]
or adapt the command line to suit the modem, then test.

copy this into gedit , then save in home directory as "sakis-connect",
```
#!/bin/sh
while [ 1 ] # loop for ever
do
reset
/usr/bin/sakis3g silent status
ret=$?
if [ "${ret}" -eq "0" ]; then
   echo "Connected."
elif [ "${ret}" -eq "6" ]; then
   /usr/bin/sakis3g silent plugged
   ret=$?
   if [ "${ret}" -eq "0" ]; then
      echo "Not connected."
      echo "trying to connect to internet"
      /usr/bin/sakis3g silent "connect" APN="3internet" # edit APN to suit,or the command to suit modem,
   else
      echo "No modem plugged."
   fi
else
   echo "Error ${ret} occurred." >> /dev/stderr
fi

sleep $((1*60)) # edit for timing this is set to check every minute
done
```call from the terminal with this command
```
sh `pwd`/sakis-connect
```Have fun, for other command line tips look at the wiki pages

---

### Post by GeorgeVita on 2010-05-02
Hi **alexfish**, very helpful thread!

Just to add some notes:

**wvdial** and dependencies are not included into CD of **9.04** and **9.10** (exists on DVD). You can install it if you have an internet connection (sudo apt-get install wvdial) or download and install the packages needed:
[wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790").

Ubuntu **9.10** initial version (liveCD) has [bug#446146]("https://bugs.launchpad.net/bugs/446146") which affects most 3g modems. An **update using any other connection** (ethernet or wifi) 'repairs' it.

Ubuntu **10.04** includes **wvdial** and dependencies but are NOT installed!
To install them read [wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790")

Regards,
George

---

### Post by alexfish on 2010-05-02
if the device requires sim or puk code , try use Network Manager or wvdial or sakis3g(sakis3g can not connect cdma devices which does not have a sim card or uses dial command #777 )

How to use PPP  
 

 example 3g using pap
 

 from the terminal
 

 sudo pppconfig
 

 select Create new connection
 
enter a name for your connection / from the keyboard hit enter for a test I used &#8220;me&#8221;
 
select Dynamic DNS ; hit enter

 select Authentication Method  ; hit enter  ;in my case my ISP uses PAP

enter user name ; hit enter ; in my case User  
 
enter password ; hit enter ; in my case mms

 select baudrate ; hit enter { accept the default shown }
 
select pulse or tone ; hit enter ;in my case Tone
 
enter your phone number ;hit enter; in my case *99#
 
Choose modem config method; YES or NO ; I selected NO, for manual because my modem has  2 control lines and uses port ttyUSB2 ; as mention above you may have to try each one if auto detect does not work
 

 after the port has been selected hit enter
 

 now look at the screen shot ; do you see the similarities as in screen shot Post #  5
 

 select ; Finished Write files and return to main menu.  
 

 Select Quit
 

 to dial your provider
 

 pon provider ; in my case ;   pon me
 

 to exit
 

 poff

or

poff me

**GPPPON:**

gpppon is a small GUI for ppp 
 

 if you have permission problem check the pppconfig &#8220;Advance Options&#8221; and check the add user

---

### Post by alexfish on 2010-05-09
[FONT=FreeMono, monospace]**Specific AT commands to **[/FONT][FONT=FreeMono, monospace]**Enable**[/FONT][FONT=FreeMono, monospace]** and **[/FONT][FONT=FreeMono, monospace]**Disable Functions on modems **[/FONT]:**INFO now Removed: FEB 2011**

Most of the safe Specific AT command are now part of up to date Connection Managers such as { Network Manager(usually installed at default) and sakis3g}

**For info retrieval :**
 suggest installing **Gammu** , it does more than SMS texting , if you have installed wammu or Phone Manager [http://live.gnome.org/PhoneManager](http://live.gnome.org/PhoneManager) 
**gammu** should be part of the installation
All available from the software center

the help and man pages will be the best GUIDE , use in conjunction with **Gammu Manual**

```
man gammu
```or
```
gammu help
```Gammu Manual / Link
[http://wammu.eu/docs/manual/](http://wammu.eu/docs/manual/)

---

### Post by alexfish on 2010-05-09
**Using a wvdial or Gnomeppp**

To set up wvdial ( first see foot of this post )

Code:

sudo wvdialconf

then will see an output like this:

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: ZTE INCORPORATED
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: ZTE INCORPORATED
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.  
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on** /dev/ttyUSB1**.  <===================**NOTE** : my modem has **two** ports **tttyUSB1** and **tttyUSB2** : So the **wvdial.conf** would have to be edited to read :**Modem = /dev/ttyUSB2 **

Modem configuration written to /etc/wvdial.conf.

**ttyUSB1**<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" ** I would Remove this entry** 
**ttyUSB2**<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

To Edit the file for your provider details

Code:

sudo gedit /etc/wvdial.conf 



 if your service provider uses an **APN** {access point name} usually GSM
 
AT+CGDCONT  - configures the correct **APN** profile : Consult your service provider
 
AT+CGDCONT=[COLOR=Blue]n[/COLOR],&#8221;IP&#8221;,&#8221;[COLOR=Blue]apn[/COLOR]&#8221;,,0,0  , 
 
For example: 
     
 AT+CGDCONT=[COLOR=Blue]4[/COLOR],&#8221;IP&#8221;,&#8221;[COLOR=Blue]Telstra.internet[/COLOR]&#8221;,,[COLOR=Blue]0[/COLOR],[COLOR=Blue]0 [/COLOR]
 

 AT+CGDCONT=[COLOR=Blue]1[/COLOR],"IP" "[COLOR=Blue]general.t-mobile.uk[/COLOR]"
 

 The init strings can  also be important for **CDMA**:: Consult your service provider or search the net 

 **Examples:**
 
from the wvdial.conf files
 
**CDMA:** from a resent post &#8220; where  Network Manager could not handle this type of connection  &#8220;
 
[Dialer wana]
Modem Type = LG EVDO Rev.A USB Modem
Modem = /dev/ttyUSB1
Baud = 9600
ISDN = 0
Init1 = AT
Init2 = ATE0V1&D2&C1S0=0
Init3 = ATS7=60
Init4 = ATS0=0
Phone = #777
Carrier Check = no
New PPPD = yes
Username = wana
Password = wana
 

 **My GSM:** Network Manager could handle this

 [Dialer tmobile] 
     Init1 = ATZ 
     Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
     Init3 = AT+CGDCONT=1,"IP" "general.t-mobile.uk" 
     Stupid Mode = 1 
     ISDN = 0 
     Phone = *99# 
     Modem = /dev/ttyUSB2 
     Modem Type = Analog Modem 
     Username = User 
     Dial Command = ATDT 
     Password = mms 
     Baud = 115200
 Dial Attempts = 3
 
**Note the difference between CDMA and GSM**

you can have several entries in wvdial  IE : to dial the entry 

CODE :

wvdial wana

or

wvdial tmobile

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Remember if your Sim Card requires a PIN code to add in the conf file " Init1 = AT+CPIN= < your pin code > **

**Things to spot with wvdial **

**May indicate PIN code required ** (use correct pin code)

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
OK
--> Modem initialized.
--> [B]Configuration does not specify a valid phone number.
[/B]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**May indicate Sim is locked , due to sending wrong code , puck code  may be required**(best solution, place sim card in mobile phone , unblock sim , disable pin or puk code security)

[I]--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
**ERROR**
--> **Invalid dial command.**[/I]
-->** Disconnecting at Wed Oct 13 13:13:24 2010**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
**Gnomeppp** is a front end to **wvdial** and easier to use from a desktop point of view. if **wvdial ** works then use same details for **gnomeppp**,

---

### Post by alexfish on 2010-05-11
[SIZE=2]**Sakis3g  :**[/SIZE] MOVED#[**5**]("http://ubuntuforums.org/showpost.php?p=9206643&postcount=5")

---

### Post by rbpyogesh on 2010-05-26
The Tips above were certainly useful...I have similar problem but Mine is a bit strange...I have a USB Mobile BB....But for mine...It is perfectly being detected in my Desktop loaded with Ubuntu 10.04...and my laptop which is loaded with 9.10....

The problem is if I upgrade my laptop to 10.04...It is not detected...But being done fine in Desktop...

Why is it so...

Can anyone help me....

---

### Post by gator2802 on 2010-05-26
> **rbpyogesh said:**
> The Tips above were certainly useful...I have similar problem but Mine is a bit strange...I have a USB Mobile BB....But for mine...It is perfectly being detected in my Desktop loaded with Ubuntu 10.04...and my laptop which is loaded with 9.10....
 
The problem is if I upgrade my laptop to 10.04...It is not detected...But being done fine in Desktop...
 
Why is it so...
 
Can anyone help me....
 
 
Reports indicate that the new linux kernel version that is part of Lucid 10.04 is not noticing certian 3 G modems.  9.10 had few issues due to using an older kernel version.

---

### Post by rbpyogesh on 2010-05-27
It is not exactly that....Mine is being noticed at my desktop but not on my Laptop...

How can it be...??

---

### Post by alexfish on 2010-05-27
> **rbpyogesh said:**
> The Tips above were certainly useful...I have similar problem but Mine is a bit strange...I have a USB Mobile BB....But for mine...It is perfectly being detected in my Desktop loaded with Ubuntu 10.04...and my laptop which is loaded with 9.10....

The problem is if I upgrade my laptop to 10.04...It is not detected...But being done fine in Desktop...

Why is it so...

Can anyone help me....

Hi 

Is this a generic problem with all USB devices or just the modem

---

### Post by rbpyogesh on 2010-05-28
Just that particular Modem....And That only on that Particular desktop...

And If I attach my phone...I could connect it to the net Normally...

I am thinking of downloading the Xfce version for now and try checking it...Because mY laptop Specs are actually very basic....

---

### Post by alexfish on 2010-06-19
[B]Editing in progress: most of what was here; now moved to Post # 2: (Thur . Feb . 24 . 2011)

How to flip USB Modems and modprobe manually[/B] +** Adding the rules to etc /udev/rules.d** And [B]Testing the connection
Note: [/B]** [7 feb 2011] **[B]this post will be replaced by a one off script ,  : the script will encompass most of what listed
need to copy and save parts : do so now:
[/B] 
REMEMBER ALL THESE ARE EXAMPLES : SUBSTITUTE THE device ID's in the examples WITH the  ID's of YOUR device : (as they say you have been warned)

to see which modules are been used or loading at runtime use the "lsmod" command from the terminal

```
lsmod
```to check if device supported , find the name of driver to the device depends , 
example of devices with option driver
```
modinfo option
```check with the ID's from the lsusb command
```
lsusb
```*Search your system to ensure the "modem-modeswitch" is in the "/lib/udev" directory , you will need this for the last part of this post ,IE :to set the udev/rules.d*

if the serial drivers have not loaded or the device has not registered as a modem try the following
```
ls -al /dev/serial/by-id/usb*
```if it comes up with an error try
Find the Mass Storage of the device[COLOR=Blue]
[/COLOR]```
ls -al /dev/disk/by-id/usb*Mass_Storage*
```or
```
ls -al /dev/disk/by-id/usb*Storage*
```example reply
 > /dev/disk/by-id/usb-HUAWEI_Mass_Storage-0:0 -> ../../[COLOR=Blue]sr2[/COLOR]Eject the device
```
eject -s /sr2
```wait for the device to settle
```
lsusb
```example reply:
> Bus 001 Device 007: ID [COLOR=Blue]12d1[/COLOR]:[COLOR=Blue]1003[/COLOR] Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA ModemNote some devices will show the same ID's as when not flipped : as the above listed device: With devices that show the same ID's always double check that the eject command has been sent , if this is not done  the drivers may not load:Although the CD TRAY does makes a handy coffee cup Holder
**............................................................................**
**For GSM :Check to see if the option drivers will load for the  device**:
Also If you have a problematic devices and the below command "**sudo modprobe option"** works then make a start-up script for the dialler to include the command
```
sudo modprobe option
```**............................................................................**
check your logfile viewer / messages . you may see something like 
> usbcore: registered new interface driver usbserial
USB Serial support registered for generic
usbcore: registered new interface driver usbserial_generic
usbserial: USB Serial Driver core
USB Serial support registered for GSM modem (1-port)
option 1-9:1.0: GSM modem (1-port) converter detected
usb 1-9: GSM modem (1-port) converter now attached to ttyUSB0
option 1-9:1.1: GSM modem (1-port) converter detected
usb 1-9: GSM modem (1-port) converter now attached to ttyUSB1
usbcore: registered new interface driver option
option: v0.7.2:USB Driver for GSM modems**............................................................................**
**For CDMA :Check to see if the ACM drivers will load for the  device**:
```
sudo modprobe cdc-acm
```**............................................................................**
For other drivers examine files
lib/modules/kernel version/kernel/drivers/usb/serial
lib/modules/kernel version/kernel/drivers/usb/class
lib/modules/kernel version /kernel/drivers/net/usb
**............................................................................**

Question: 
Sometimes my device is recognized on the system , and sometimes not

Answer  : 
Sometime it occurs if the device was plugged in at boot and then later inserted after a boot: also notable if switching between windows and Linux
[COLOR=Blue]Do The Above procedure[/COLOR] . Remember to connect the device after boot

Question:

my device is recognized on the system but the Network Manager can't find it , or will not connect

Answer:

this can occur if the device was plugged in at boot , the result been the device has automatically booted in and connected through the pppd
Kill the pppd daemon
```
Killall pppd
```[COLOR=Blue]

[COLOR=Black]Remember to connect the device after boot

[/COLOR][/COLOR][COLOR=Blue][COLOR=Black][B]Modem-Modeswitch : 
[/B][/COLOR][/COLOR][COLOR=Blue][COLOR=Black]**setting the  udev rules.d**[/COLOR][/COLOR]

Please read:  [now obsolete]("http://markmail.org/message/k662fucn5ab2gfc5"), Modem-modeswitch for providing similar  services only for a limited subset of devices **Usb_ModeSwitch**  does.
**May be totally depreciated in Ubuntu 10.10**.

depreciated: rules now removed (as of above date)

Can also suggest keep up date with latest news as regards  HAL and  UDEV , could be someday Hal nomore :
Note: for those looking Toward HAL to find ,Device info, May find ALL info is listing, as to the device Capabilities, can try Sakis3g, to update HAL, look through the MENU options
Sakis3g will still work in the absence of HAL ( says he , I think)

use the **lsusb** command to find the device details
[COLOR=Blue][COLOR=Black]

**ZTE devices:Example **
[/COLOR][/COLOR]```
sudo gedit /etc/udev/rules.d/zte_eject.rules
```[COLOR=Blue][COLOR=Black]add the following line(edit the [/COLOR][/COLOR][COLOR=Blue][COLOR=Black]SYSFS{idVendor}=="[COLOR=Blue]ID[/COLOR]",  SYSFS{idProduct}=="[COLOR=Blue]ID[/COLOR]"[/COLOR][/COLOR] according to device 
```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule" 
```[COLOR=Blue][COLOR=Black]The first Error I made was to copy an example that did not end with [COLOR=Blue]".rules"[COLOR=Black] . [/COLOR][/COLOR]

[B]Notes:

[/B]use of the "[COLOR=Blue]**ls -al /dev/serial/by-id/usb***[/COLOR]" lists the orientation of the tty ports

**Incorrect switching:** Example
The ports have reversed ,although the log file messages shows them in sequence 
The results in the network manager etc will be unable to connect

/dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../[COLOR=Blue]ttyUSB1[/COLOR]
/dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../[COLOR=Blue]ttyUSB0
[/COLOR]
option 1-10:1.1: GSM modem (1-port) converter detected
usb 1-10: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB0[/COLOR]
option 1-10:1.0: GSM modem (1-port) converter detected
usb 1-10: GSM modem (1-port) converter now attached to [COLOR=Blue]ttyUSB1[/COLOR]

**Correct switching:**
/dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
/dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1

you can also monitor the device with the lsusb -t command [ note the changes]

[B]If the device is listing incorrectly and Still recognized (try to resolve the issue ) if a resolve can't be found and the Network Manager is failing to connect Fix: Use Alternate Method of dial up where you can choose the ttyport, you will have to test each port ( report bug to Network Manager RE modem manager , {can be checked be testing the CTS,DCD and DSR lines of the serial port} )
~~~~~~~~~~~~~~~~~~~~~
[/B][/COLOR][/COLOR]                                  **Statserial:**
 
using **statseria**l to check the status line of your modem
 
Examples:
 ```
statserial /dev/ttyUSB1
```response
 > Device: /dev/ttyUSB1 
Signal  Pin  Pin  Direction  Status  Full 
 Name    (25) (9)  (computer)         Name 
 -----   ---  ---  ---------  ------  ----- 
 FG       1    -      -           -   Frame Ground 
 TxD      2    3      out         -   Transmit Data 
 RxD      3    2      in          -   Receive  Data 
 RTS      4    7      out         1   Request To Send 
 [COLOR=Blue]CTS      5    8      in          0   Clear To Send [/COLOR]
 [COLOR=Blue]DSR      6    6      in          0   Data Set Ready [/COLOR]
 GND      7    5      -           -   Signal Ground 
 [COLOR=Blue]DCD      8    1      in          0   Data Carrier Detect [/COLOR]
 DTR     20    4      out         1   Data Terminal Ready 
 RI      22    9      in          0   Ring Indicator  ```
statserial /dev/ttyUSB2
``` response : Note this out put Indicates it could be the modem
 > Device: /dev/ttyUSB2 
  Signal  Pin  Pin  Direction  Status  Full 
 Name    (25) (9)  (computer)         Name 
 -----   ---  ---  ---------  ------  ----- 
 FG       1    -      -           -   Frame Ground 
 TxD      2    3      out         -   Transmit Data 
 RxD      3    2      in          -   Receive  Data 
 RTS      4    7      out         1   Request To Send 
 [COLOR=Blue]CTS      5    8      in          1   Clear To Send [/COLOR]
 [COLOR=Blue]DSR      6    6      in          1   Data Set Ready[/COLOR] 
 GND      7    5      -           -   Signal Ground 
 [COLOR=Blue]DCD      8    1      in          1   Data Carrier Detect [/COLOR]
 DTR     20    4      out         1   Data Terminal Ready 
 RI      22    9      in          0   Ring Indicator  Test the modem : Even if the statserial does not show output as above/ testing each ttyport : Can only assume modem has been Pre-Probed and left in a state where these lines have been suspended
[B]
:::: rest removed
[/B]

---

### Post by im.saravanan on 2010-06-21
:confused:Hi i have a usb Micromax mmx3000G usb 3 G modem. In win xp--
 
As mass storage its id is Vid_05c6&Pid_f000
 
and as mode its id is Vid_05c6&Pid_9000
 
in ubuntu netbook remix 10.4 when i insert and immediately give the command lsusb
 
its id  is shown as 05c6 x f000  and on subsequent lsusb its id has changed to 05c6 x 9000. So i consider the switching of mode is done.
 
Now when i run wvdialconf wvdial.conf in /usr/bin it is not finding the modem. at the end it says like 'have you used setserial ........' 
 
dmesg -- does not show any modem device. it is shown as storage device. 
 
How to go about it.

---

### Post by alexfish on 2010-06-21
Hi im.saravanan

I think you are correct about the device having been switched

what is the result of this code from the terminal
```
ls -al /dev/serial/by-id/*
```

---

### Post by Whitston on 2010-07-02
I am hoping that GeorgeVita will pick up on this cry for help, but failing that, any kind soul will do!

My netbook is running 10.4 and I have updated it through update manager. I have bought an o2 dongle (MF100) on payandgo.  It is ZTE device.  I went into Network Manager and entered the details and I now get o2 payandgo as an option under the network manager.  I read some of GeorgeVita's earlier posts and noted that I should not enter the keyring password when asked, and cancelling this request brings up a request for the ZTE password.  I enter payandgo (which was entered by Ubuntu when I created the link).  It tries to connect, but does not.

Also, when Ubuntu created the o2 link, it put *99# as the phone number.  I have tried with this, and also inserted the actual number that came with the dongle.

Is there any hope for me?  Not sure I can cope with difficult stuff like wvdial (which I saw on another post).

Thanks in anticpation, 

Jim Whitston

---

### Post by GeorgeVita on 2010-07-03
Hi **Whitston**,
as we do not have the same modem it is difficult to find a 100% solution. From your description as you had tried those stated in this thread by **alexfish**, just try to remove the modem, wait some seconds attach it again and retry to connect. 

If the problem still exists, try to set the mobile broadband connection again (remove modem, delete all existing mobile broadband connections, reboot, wait for the sysytem to fully load, attach modem, setup again your connection.

If again you have the problem I propose to open a new thread to **[Networking & Wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336")** stating **your modem type on title**, just in case another user of the same modem will see it.

Good Luck!

Regards,
George

---

### Post by Whitston on 2010-07-05
Thaks **GeorgeVita**

Have tried all you suggested above.  This time the system tried to connect for a longer time, but in the end failed.   I will try a new thread as you suggest.  Thanks for your help.

Jim Whitston

---

### Post by JackAbear on 2010-07-06
bump

---

### Post by kkfok1 on 2010-07-15
> Device not recognised in the Network Manager : follow the below . Also Checkout Post #16

    * If it is not recognised and an icon appears and the desktop try right click with mouse and "eject" or "safely remove" the device then see if will configure
    * There is a difference between the "eject" and "safely remove". so it is best to monitor the effect it has on your Modem and the Network Manager
    * To help you to understand why some device are not recognised on a Linux the system :Read info at the site relating to the usb modeswitch
    * If nothing happens , open up the terminal and enter this command

I have a ZTE MF102 USB modem and running 10.04 with modeswitch installed (before installation of modeswitch the modem does not work). I have intermittent problem that the modem recognise by Network Manager.

When I do lsusb :
Bus 002 Device 002: ID 19d2:0031 ONDA Communication S.p.A. ZTE MF636

But Network Manager some times not recognise the modem, however, after I reboot the laptop once or twice, then the modem can be recognised by network manager and connected to the service provider automatically. 

I am just not comfortable with this situation that "some times work and some times not work". Also, there isn't an icon of the modem for me to eject / safely remove as per the above "quote"

I would appreciate some advise on :

1. How to ensure the modem can work every time I plug it into my laptop (if not, please provide some way to monitor what went wrong. My personal observation is the pppd does not start automatically when the modem not working)

2. How to eject/safely remove/shutdown the modem gracefully so that I can plug it in again and it will work (at the moment when I unplug the modem, and put it back later, it will not work, and I have to reboot twice to make it work again)

BTW, I just use Network Manager to configure so dialing is not a problem. The problem just at the initialization step that Network Manager not recognise the modem (or pppd not start, I assume Network Manager control to start pppd, or the other way round???)

Thanks

---

### Post by JackAbear on 2010-07-15
Y'all check out my new POST below, though I admit the 0031 puzles me, I think I saw that  showing up  also when I was trying with WVdial at the beginning of my quest !

[http://ubuntuforums.org/showthread.php?p=9593938#post9593938](http://ubuntuforums.org/showthread.php?p=9593938#post9593938)

Even though the method is good, Rogers stick is extremely intermitent in my area, and cuts out often even on the Windhose XP setup, and when it cuts out  it remains at zero kb/s and you cannot browse, until you shut down it's software, re-load the software, and hope it will connect the next time. sometime you have to wait a few hours and try again, 
You can can expect the same thing with Ubuntu, not ubuntu's fault in most  cases...and restarting ubuntu is the equivalent of re-loading the software in a windows set-up. I would have had to write another three pages to cover all that in detail...And  the stick slows down when hot, and shuts off when too hot...so put a fan on it if you download long updates.and stuff..
Hope that helps also

---

### Post by alexfish on 2010-07-17
Regarding to post by "Jack A bear" and the link ( interesting fix "Ubuntu Studio" { Network Manager may not be installed at default )
if you have Audio Problems by following the advice in the link Please refer to [Ubuntu Studio]("http://ubuntuforums.org/forumdisplay.php?f=335")
Also
[http://ubuntuforums.org/showthread.php?t=1508967](http://ubuntuforums.org/showthread.php?t=1508967)
[http://ubuntuforums.org/showthread.php?t=1525705](http://ubuntuforums.org/showthread.php?t=1525705)

always check your versions for  distro
 
**group 1 :**
match versions **Network Manager**
 
libnm-util1...................... match   
libnm-glib2..................... match 
network-manager........... match  
network-manager-gnome match 
modemmanager............. match ....Not mentioned in the link / Network Manager dependency .. for as said... manages your modem

**group2**:
match versions **policykit-gnome**

libpolkit-dbus2........ match
libpolkit-grant2....... match
libpolkit2 ............... match
libpolkit-gnome0..... no match .check for latest version for your distro

[FONT=Verdana][SIZE=2][http://packages.ubuntu.com/](http://packages.ubuntu.com/)

[http://live.gnome.org/PolicyKit](http://live.gnome.org/PolicyKit)

 [/SIZE][/FONT][SIZE=2][B]Also checkout  gksu-polkit

[/B][U][http://www.nongnu.org/gksu/](http://www.nongnu.org/gksu/)
[/U] 
[http://live.gnome.org/gksu](http://live.gnome.org/gksu)[/SIZE]   
 
[FONT=Verdana][SIZE=2] 
policykit-gnome and Network Manager from synaptic  below screen shot with dependencies

[/SIZE][/FONT]

---

### Post by alexfish on 2010-07-18
**How to use the dev/tty for communicating with the modem**

Recommend usage : absence of wvdial 

Warning if The Device is required to use <CID> dialing , refrain from loading the [COLOR=Red]CGDCONT[/COLOR] registers  [COLOR=Red]AT+CGDCONT[/COLOR]
 
forgot your AT commands see foot of post #[**2**]("http://ubuntuforums.org/showpost.php?p=9201405&postcount=2")
  for downloads

 If you have read the rest of this thread and don't have a means of connecting this may help

**Part one:** 
 a simple GSM connection
 
Edit the **tty** ports to suit your modem :                            **Don't know how to**  check back at post #**[16]("http://ubuntuforums.org/showpost.php?p=9483244&postcount=16")** 

  AT commands are sent to the modem via this command &#8220;echo -e "AT command\r" > /dev/ttyUSB2&#8221;
 
try them from the terminal

**example**
open up first terminal to monitor the modem

**Code:**

tr -s "\n" < /dev/ttyUSB2
 
 open up a second terminal

**code:**
 echo -e "ATZ\r" > /dev/ttyUSB2
 
so the below script can easily be adapted to suit your needs

#!/bin/sh
# edit the tty port to suit the modem
# optional open a terminal to monitor the connection and enter this command
# needed if trying to find cid profiles etc.
# Code:
# tr -s "\n" < /dev/ttyUSB2

echo "Ctrl + c to exit"
echo " "
echo -e "ATZ\r" > /dev/ttyUSB2 # reset the modem
echo "======> sending ATZ"
# find the [COLOR=Red]CGDCONT[/COLOR] profiles for <cid> dialing [COLOR=Red]AT+CGDCONT?[/COLOR]
echo "searching <cid> profiles"
echo -e "[COLOR=Red]AT+CGDCONT[/COLOR]?\r" > /dev/ttyUSB2 # see example response below , Also Demonstrated in the First Post


echo "=======>sending ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
echo -e "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0\r" > /dev/ttyUSB2

#echo -e "[COLOR=Red]AT+CGDCONT[/COLOR]=1,\"IP\" \"[COLOR=Blue]your service providers[/COLOR] APN\"\r" > /dev/ttyUSB2
echo -e "[COLOR=Red]AT+CGDCONT[/COLOR]=1,\"IP\" \"[COLOR=Blue]general.t-mobile.uk[/COLOR]\"\r" > /dev/ttyUSB2 # disable with # if using cid

echo "=======>dialing"
echo -e "ATDT*99#\r" > /dev/ttyUSB2 # or use the <cid> method of dialing

# echo -e "ATDT*99***1#\r" > /dev/ttyUSB2 OR for CDMA :dial number = #777

echo "=======>attempting Connecting to network"
sudo pppd ttyUSB2 115200 nodetach defaultroute noipdefault noauth lock usepeerdns

# AUTHENTICATION 
# If noauth works, use that, otherwise you have to pass 
# the user name and password. This is an example of a 
# standard Cingular user/pw combo 
# sudo pppd ttyUSB2 115200 nodetach defaultroute noipdefault noauth lock usepeerdns user [EMAIL="ISPDA@CINGULARGPRS.COM"]ISPDA@CINGULARGPRS.COM[/EMAIL] password CINGULAR1
#############################################################################################
# Usernames and passwords
# sudo gedit/etc/ppp/chap-secrets - Add your " username and password" for authentication using CHAP if your isp requires
# sudo gedit/etc/ppp/pap-secrets - Add your " username and password" for  authentication using PAP if your isp requires
# example "User" * "mms" 
######################################################################################
# example response use for <cid> dialing . 
# +CGDCONT: 1,"IP","[COLOR=Blue]general.t-mobile.uk[/COLOR]","0.0.0.0",0,0 can try ATDT*99# or ATDT*99***1#
# +CGDCONT: 2,"IP","payandgo.o2.co.uk","0.0.0.0",0,0  can try ATDT*99***2#
# +CGDCONT: 3,"IP","m-bb.o2.co.uk","0.0.0.0",0,0 can try ATDT*99***3#
# and so on 
#######################################################################################

**AT+CGDCONT:set PDP format**    : Not required by CDMA ; Lines containing this command in the above script should be  be omitted

**Description :**This command is used to set GPRS&#8217;s PDP format. 
 Format  : AT+CGDCONT=cid, type, APN[,PDP_ADDR] 
 **Parameters **
cid: used to define PDP number; min.:1. 
 type: PDP packet type, IP: use TCP/IP packet. 
 APN: access node network name.. 
 PDP_ADDR: IP address specified by user (optional). 

 **Example :**
 AT+CGDCONT=1, "IP","CMNET"
 
ATDT*99#   
  &#8230;......           
 Connect
 
**CDMA:**
To connect via 1xRTT and use your provider as an ISP, use the following values:
Number     #777
Username     <number>@<provider>
Password     <pwd>

In all cases, replace <number> with your raw phone number: (555) 123-1234 would be '5551231234'

<provider> and <pwd> vary based on your provider.
Provider     <provider>     <pwd>
Verizon     vzw3g.com     vzw 
Alltel     alltel.com     allltel

If you are using Sprint, Username is your Vision login and Password is your Vision password. The number to dial remains #777.
Why to avoid 1xRTT

1xRTT is known to be a weak point by most carriers, and it is also an obsolete technology. Excessive or continual use in areas that have known EV-DO coverage will be discovered and billed as illegitimate data usage.

**EV-DO**

EV-DO is the current choice of CDMA providers for data services, and offers significant speed boosts over 1xRTT. 
Details

To connect via EV-DO and use your provider as an ISP, use the following values:
Number     #777
Username     <number>@<provider>
Password     <pwd>

In all cases, replace <number> with your raw phone number: (555) 123-1234 would be '5551231234'

<provider> and <pwd> vary based on your provider.
Provider     <provider>     <pwd>
Verizon     vzw3g.com     vzw
Alltel     alltel.com     allltel

If you are using Sprint, Username is your Vision login and Password is your Vision password. The number to dial remains #777.

**Baud Rates **: some are fixed by your isp , However the device may be influenced by the AT command AT+IPR

AT+IPR=? : Query baudrates
AT+IPR? : Query current baud rate

**To set the baud rate**
Example:
AT+IPR=[COLOR=Blue]115200[/COLOR]

note the influence of [COLOR=#0000ff]baud rate[/COLOR] on the call to the pppd IE :sudo pppd ttyUSB2 [COLOR=#0000ff]115200[/COLOR] nodetach defaultroute noipdefault noauth lock usepeerdns .[COLOR=Blue]Both should match
[/COLOR]  
Tip: if the device has a memory card or text storage on the sim or memory , save the file to the device, 
 You now own  a " UBUNTU " compatable  USB Mobile Dongle thingy ma jig. well almost , just need to hack that mass storage device
connection screenshot below

---

### Post by alexfish on 2010-07-19
[B]Example of retrieving 3g sms texts from the modem using the terminal 

may be relevant see
[/B]   	 	 	 	 	 	  Post #**[11]("http://ubuntuforums.org/showpost.php?p=9660332&postcount=11")  **[http://ubuntuforums.org/showthread.php?t=1528185&page=2](http://ubuntuforums.org/showthread.php?t=1528185&page=2)
 

Below are the standard AT commands for listing 3g sms texts
Please refer to the AT command reference guide for your modem
This can be converted to a script { if done introduce the command " sleep 1 " between each " echo -e "ATCODE\r" > /dev/ttyUSB1"
edit tty port for the modem

open up first terminal and enter the command

Code:
tr -s "\n" < /dev/ttyUSB1

open up second terminal and enter the following commands, the first terminal should show the results

Code:
echo -e "ATZ\r" > /dev/ttyUSB1

check if pin  code required

Code:
echo -e "AT+CPIN?\r" > /dev/ttyUSB1

enter pin number if required, can also be used in the above connection script

Code:
echo -e "AT+CPIN=<pincode>\r" > /dev/ttyUSB1

set echo command for the modem

Code:
echo -e "ATE\r" > /dev/ttyUSB1

find locations of sms texts

Code:
echo -e "AT+CPMS?\r" > /dev/ttyUSB1 

set modem to sms text mode

Code: 
echo -e "AT+CMGF=1\r" > /dev/ttyUSB1

set the location for sms text , edit according to the response of the echo -e "AT+CPMS?\r" > /dev/ttyUSB1 command

Code:
echo -e "AT+CPMS=\"ME\"\r" > /dev/ttyUSB1

list all sms texts

Code:
echo -e "AT+CMGL=\"ALL\"\r" > /dev/ttyUSB1

Reminder reading the AT command reference guide for your modem helps

---

### Post by JackAbear on 2010-07-22
> **alexfish said:**
> Regarding to post by "Jack A bear" and the link ( interesting fix "Ubuntu Studio" { Network Manager may not be installed at default )
if you have Audio Problems by following the advice in the link Please refer to [Ubuntu Studio]("http://ubuntuforums.org/forumdisplay.php?f=335")
Also
[http://ubuntuforums.org/showthread.php?t=1508967](http://ubuntuforums.org/showthread.php?t=1508967)
[http://ubuntuforums.org/showthread.php?t=1525705](http://ubuntuforums.org/showthread.php?t=1525705)

always check your versions for  distro
 
**group 1 :**
match versions **Network Manager**
 
libnm-util1...................... match   
libnm-glib2..................... match 
network-manager........... match  
network-manager-gnome match 
modemmanager............. match ....Not mentioned in the link / Network Manager dependency .. for as said... manages your modem

**group2**:
match versions **policykit-gnome**

libpolkit-dbus2........ match
libpolkit-grant2....... match
libpolkit2 ............... match
libpolkit-gnome0..... no match .check for latest version for your distro

[FONT=Verdana][SIZE=2][http://packages.ubuntu.com/](http://packages.ubuntu.com/)

[http://live.gnome.org/PolicyKit](http://live.gnome.org/PolicyKit)

 [/SIZE][/FONT][SIZE=2][B]Also checkout  gksu-polkit

[/B][U][http://www.nongnu.org/gksu/](http://www.nongnu.org/gksu/)
[/U] 
[http://live.gnome.org/gksu](http://live.gnome.org/gksu)[/SIZE]   
 
[FONT=Verdana][SIZE=2] 
policykit-gnome and Network Manager from synaptic  below screen shot with dependencies

[/SIZE][/FONT]

Thank you alexfish for this very generous supply of information on this topic, I checked some of this out,... but being the noob that I am it will take me at least three months of hands on to digest all that...., but that's ok!
thanks also for pointing out the audio bugs involved and  the how to fix links.

I now understand that I was very lucky, and that my homemade method for wireless worked only because UbuntuStudio's update manager picked up the  slight discrepancies you mentioned and automatically slated libpolkit-gnome0 for removal along with one of the libnm's , before doing the initial series of updates....it  did exactly what I was hoping for, with fingers  crossed on both hands...it also installed the modemmanager which I had not picked up on....very smart operating system isn't it?
I will copy this  helpful  thread to an open office file, for ongoing reference , in order to study all aspects.
BTW, If you just happen to know of a link that explains where to get  and how to install ASIO drivers for MOTU TRAVELER firewire  or (2nd option)Creative labs SOUND BLASTER pci card, I would certainly  welcome that information.

Thanks again,
Jack A bear

---

### Post by JohnBUK on 2010-07-22
> **Whitston said:**
> I am hoping that GeorgeVita will pick up on this cry for help, but failing that, any kind soul will do!

My netbook is running 10.4 and I have updated it through update manager. I have bought an o2 dongle (MF100) on payandgo.  It is ZTE device.  I went into Network Manager and entered the details and I now get o2 payandgo as an option under the network manager.  I read some of GeorgeVita's earlier posts and noted that I should not enter the keyring password when asked, and cancelling this request brings up a request for the ZTE password.  I enter payandgo (which was entered by Ubuntu when I created the link).  It tries to connect, but does not.

Also, when Ubuntu created the o2 link, it put *99# as the phone number.  I have tried with this, and also inserted the actual number that came with the dongle.

Is there any hope for me?  Not sure I can cope with difficult stuff like wvdial (which I saw on another post).

Thanks in anticpation, 

Jim Whitston

Re the "*99#" I used that and added "44791xxxxxxx" as the number (without quotes and xxxs) and it worked for me on Ubuntu. My dongle is the ZTE MF627 from 3.
John

---

### Post by JohnBUK on 2010-07-22
Am running Ubuntu 10.04 and have tried to get my ZTE MF627 dongle from "3" working to no avail for months. I have to load up Windows Vista to use!
Today I went to the "3" website where they have new software for this dongle - (in theory it is not yet available for Vista but I downloaded the file anyway). I installed the software in my dongle whilst in Vista and then started Ubuntu and re-entered the dongle in "Network Connections". Lo and behold IT WORKED. I hasten to add I'm a total dunce on Ubuntu and command lines etc so cannot explain why - only that it just works.
JohnB

---

### Post by llamahunter on 2010-07-22
Hi there-

Having trouble with Ubuntu 10.04 and my Sierra Wireless 598U CDMA USB modem.  Worked like a charm in 9.10, now very very flakey (but occasionally works) in 10.04.  It seems to be recognized and establish a working connection almost all the tim, but then 80+% of the time drops the connection 5 seconds after establishing it.  I have to unplug the USB modem and plug it back in to try again.  I filed (and have been updating) a bug with launchpad, but no one seems to be looking at it.

Any ideas?  Would really like this to work smoothly again.

Richard

---

### Post by alexfish on 2010-07-22
Hi johnBUK

RE: Posts #29 and #30

welcome to the forum

Your post is Certainly most welcome and useful , there have been numerous threads and posts regarding 3 at the Networking and Wireless , if you frequent these forums your input may be appreciated by other members trying to get connected with 3

once again thanks

regards alexfish

---

### Post by JackAbear on 2010-07-23
> **llamahunter said:**
> Hi there-

Having trouble with Ubuntu 10.04 and my Sierra Wireless 598U CDMA USB modem.  Worked like a charm in 9.10, now very very flakey (but occasionally works) in 10.04.  It seems to be recognized and establish a working connection almost all the tim, but then 80+% of the time drops the connection 5 seconds after establishing it.  I have to unplug the USB modem and plug it back in to try again.  I filed (and have been updating) a bug with launchpad, but no one seems to be looking at it.

Any ideas?  Would really like this to work smoothly again.

Richard

I also get similar problem quite often with my mf668, being on the  outskirts, i.e. 4 clicks oustide of recognized 7 click service area, whether I'm using it with win 7 64, windows XP home, or UbuntuStudio 10.04 64bit.  And I only get service with the rocket stick on a 6' extension going to a very narrow (6cm) 3 inch square area in my dinning room window  overlooking the valley. move it one inch off and it goes  green instead of blue, another inch or anywhere else in the house and it stays red...no signal at all...
On good days I get up to 2mb/s, on poor days I get between 2 kb/s to 50 kb/s with frequent drop offs,all  depending it seems on wind direction, humidity( air density) skips off thick cloud cover, stick itself getting too hot from the sun... etc. (6 ft extension also creates resistance and worsens my reception, but what can you do?)
So, my question to you  is, have you changed the position or angle of your stick in any way?
Just food for thought, hope this info helps,
My two beans

---

### Post by JohnBUK on 2010-07-23
Hi Alexfish, thank you. I do frequent the site as many people have been very kind and helpful to me. I have very little technical knowledge re Linux / Ubuntu but am delighted to "repay" in my own small way!!
John

---

### Post by BigScaryDragon on 2010-08-16
> 
I am hoping that GeorgeVita will pick up on this cry for help, but failing that, any kind soul will do!

My netbook is running 10.4 and I have updated it through update manager. I have bought an o2 dongle (MF100) on payandgo. It is ZTE device. I went into Network Manager and entered the details and I now get o2 payandgo as an option under the network manager. I read some of GeorgeVita's earlier posts and noted that I should not enter the keyring password when asked, and cancelling this request brings up a request for the ZTE password. I enter payandgo (which was entered by Ubuntu when I created the link). It tries to connect, but does not.

Also, when Ubuntu created the o2 link, it put *99# as the phone number. I have tried with this, and also inserted the actual number that came with the dongle.

Is there any hope for me? Not sure I can cope with difficult stuff like wvdial (which I saw on another post).

Thanks in anticpation, 

Jim Whitston


I had exactly the same issue (with the MF100 too), and solved it following these steps (lifted from [http://www.redirecttonull.com/?p=202](http://www.redirecttonull.com/?p=202)):

[LIST=1]
[*]Plug in the USB dongle, and wait 30 seconds for it to be detected and initialised
[*]Go to System -> Preferences -> Network Connections.
[*]Click the Mobile Broadband tab
[*]Click “Add” to start the wizard to add the USB dongle
[*]The first page should have “ZTE Incorporated ZTE WCDMA Technologies MSM” selected in the device drop down. Click “Forward”
[*]Select your country. Click “Forward”
[*]Select the provider (O2). Click “Forward”
[*]Select your plan (Pay and Go (Prepaid)). Click “Forward”
[*]Click “Apply”
[*]A new window will pop up. Under the “Mobile Broadband” tab change the defaults to the following:
Number: *99#
Username: o2bb
Password: password
APN: m-bb.o2.co.uk
Network: (leave blank)
PIN: (leave blank)

[*]Click “Apply” to close the new window
[*]Click “OK” to close the “Network Connections” window
[/LIST]

---

### Post by alexfish on 2010-10-11
[B]Reference Ubuntu Maverick Meerkat :Moved to Post #2
[/B][COLOR=Blue][B][COLOR=Black]
[/COLOR][/B][/COLOR]

---

### Post by toloykhan on 2010-10-14
[QTUOE=alexfish;9283123][SIZE=2]**Sakis3g  :**[/SIZE]

 [SIZE=2]This is a  recent dialler so as to its usage I have listed part of the Wiki site , well worth a visit

[/SIZE]  [SIZE=2]Advantages of sakis3g  click on the “Sakis3G script is all about”[/SIZE]

If you have installed usb_modeswitch  try to disable it , since the usb_modeswitch is part of Sakis3g.[QTUOE]
thanx so much this was realy helpful for me I use it to initilizing my hawawi 3g data card witch haven't software driver for ubuntu thanx again .

---

### Post by rasaiashok on 2010-11-03
> **alexfish said:**
> [SIZE=2]**Sakis3g  :**[/SIZE]

 [SIZE=2]This is a  recent dialler so as to its usage I have listed part of the Wiki site , well worth a visit

[/SIZE]  [SIZE=2]Advantages of sakis3g  click on the &#8220;Sakis3G script is all about&#8221;[/SIZE]

If you have installed usb_modeswitch  try to disable it , since the usb_modeswitch is part of Sakis3g.


[SIZE=2]**Getting started  **[/SIZE]**:**

 
[LIST]
[*]Read what [Sakis3G     script is all about]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_script").
[*][Installation     guide]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation").
[*]Locate [user     interface]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_UI") best fitting your environment, or explore its [command     line]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_invocation") powers.
[/LIST]
 [SIZE=2]**Getting support  **[/SIZE]:

 
[LIST]
[*]Check if your [operator]("http://wiki.sakis3g.org/wiki/index.php?title=Operator")     is found within [list     of known operators]("http://wiki.sakis3g.org/wiki/index.php?title=Known_operators"), or [information     you need to collect]("http://wiki.sakis3g.org/wiki/index.php?title=APN") if it is not.
[*]Learn how to [receive     support]("http://wiki.sakis3g.org/wiki/index.php?title=Category:Support").
[/LIST]
 [SIZE=2]**Read more  **[/SIZE]:

 
[LIST]
[*]Read [Sakis3G     manual]("http://wiki.sakis3g.org/wiki/index.php?title=Category:Manual").
[*]Check out [usage     guides]("http://wiki.sakis3g.org/wiki/index.php?title=Category:Usage_guides").
[*]Read all about [dependencies     and requirements]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_dependencies").
[*]How to [recompile     it]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_compilation") if necessary.
[*]Learn how to [configure     it]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_configuration").
[*][Frequently Asked Questions]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_faq").
[/LIST]
 [http://wiki.sakis3g.org/wiki/index.php?title=Main_Page](http://wiki.sakis3g.org/wiki/index.php?title=Main_Page)

**Forum:**
[http://forum.sakis3g.org/smf/index.php](http://forum.sakis3g.org/smf/index.php)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[SIZE=2]**How to install latest version** in  ** Ubuntu**:   . Possibly **Sakis3g **0.2.0e[/SIZE] . now includes usb_modeswitch " Version 1.1.3 (C) Josua Dietze 2010"

[SIZE=2]**From the terminal:**[/SIZE]
[SIZE=2]
sudo bash

cd /usr/bin[/SIZE] [SIZE=2]

wget '[/SIZE] [SIZE=2][http://www.sakis3g.org/versions/latest/sakis3g.gz']("http://www.sakis3g.org/versions/latest/sakis3g.gz%27")

echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c[/SIZE] [SIZE=2]

**You should see:**[/SIZE]  [SIZE=2] sakis3g.gz: OK

gunzip sakis3g.gz[/SIZE] [SIZE=2]

chmod +x sakis3g[/SIZE] 


then run sakis3g from the terminal

Code:

sakis3g

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 
[B]

Note :[/B] Normally I do not recommend a preferred use of software : but I could recommend trying Sakis3g , if your connection is 3g that is
**Sakis3g + Netspeed + Wammu will give you a powerful set** : can  only but try


**Available options are:**

CONNECT
    Connect with 3G
PREPARE
    Only prepare modem (Setup + PIN unlock + Register Network + Update HAL)
SETUP
    Only setup modem (Switch + Load module + Setup tty)
SWITCH
    Only switch modem (if applicable)
COMPILE
    Compile embedded Usb-ModeSwitch
DESKTOP
    Create desktop shortcut
ABOUT
    About Sakis3G
HELP
    Show help

For Command line usage :See also: [Examples]("http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_invocation#Examples")
Sir
I am using Ubuntu 10.10 I am living in India. I am using BSNL USB dial up Modem. It works Windows XP. But it does not connect Ubuntu 10.10. Please give me Idea.

---

### Post by jdcrownover on 2010-11-06
Wow, looonnnngggg post.  A prime example of why I have NOT yet made Ubuntu my primary operating system -- there is NO SINGLE GOOD INSTALL APPLICATION available.

I've been looking around trying to figure out how to get my Options Velocity modem working.  I see lots of suggestions with lots of packages, some of which I have install, but most of these require you to KNOW LINUX AT THE SYSTEM LEVEL to do anything.  THEY DON'T EVEN TELL YOU WHICH DIRECTORY YOU NEED TO PUT STUFF IN.

I read a post made in JANUARY 2010 about ZeroCD.  Here it is 11 months later, and there is STILL NOTHING IN THE UBUNTU UPDATES which allows my zeroCD to operate.

And I haven't even attempted yet to attach my peripheral devices to my Ubuntu laptop, mainly because I now expect the same LACK OF SUPPORT for them as well.

PS - I'm writing this from my WINDOWS 7 laptop, where my Options Velocity modem INSTALL WITH NO PROBLEMS AT ALL.

---

### Post by GeorgeVita on 2010-11-06
> **jdcrownover said:**
> ...I've been looking around trying to figure out how to get my Options Velocity modem working...
Hi **jdcrownover**, welcome to this forum.
I fully understand your problem with your specific 3G modem (and many other also). Some of us got tired to make our modems 'working quite good', gain some 'linux' knowledge from these tests and tried to help other people to connect. 

Unfortunately these efforts are just 'history' when you try a 'compatible' 3G modem! As most manufacturers do not provide technical info to developers this 'compatibility' is a result of painful tries and/or number of modems used by other linux users.

Regards,
George

---

### Post by tarekmg on 2010-11-25
[LEFT]I am trying to connect Huawei E180 to Ubuntu 10.10 using Acer Aspire 3500 laptop. The same was working fine on Ubuntu 9.04 but since upgrading to 10.10 the Network Connection Manager Icon in the top panel does not show the connection name. When I run [/LEFT]
  [LEFT]dmesg | grep -e "modem" -e "tty"[/LEFT]
  [LEFT]I receive only the following line and the remain lines is not listed[/LEFT]
  [LEFT][ 0.000000] console [tty0] enabled[/LEFT]
  [LEFT]How can I make my modem work again?[/LEFT]

---

### Post by alexfish on 2010-11-25
Hi tarekmg

Have a you read  post  #[**36**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

also have you read through first post 

alexfish

---

### Post by Com_2_Reset on 2011-01-11
Hello alexfish,

I got the same problem. I have read some of the posts you mentioned, but what i got is confusing?

[http://ubuntuforums.org/showthread.php?t=1663833](http://ubuntuforums.org/showthread.php?t=1663833)

---

### Post by larrybalz on 2011-01-13
Thanks.. This post was really helpfull

---

### Post by ledzpg on 2011-01-13
I think it's a good idea to have a list of known compatible "out-of-box" and devices that requires manual intervention to work; maybe a Wiki.
Is there something like this already?

---

### Post by theism on 2011-01-17
yea, check out the info on this wiki:

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

---

### Post by piment on 2011-01-28
**Telstra Elite Mobile Broadband working on Ubuntu 10.10**

I wanted mobile broadband during my travels in Australia so I went into the Telstra store in Perth, and tested the Telstra Elite Prepaid mobile broadband on my netbook (I am running Ubuntu 10.10 on an Asus Eee PC 901)

I plugged the USB modem into my netbook, went into Applications > Network Connections > Mobile Broadband and clicked on the "Add" button. 

In the "Set up a mobile broadband connection" screen, I ensured that the options ZTE WCDMA Technologies MSM > Australia > Telstra were selected, then on the "choose your billing plan" screen, I selected the option "my plan is not listed..." and typed in the APN as "telstra.internet". I confirmed my mobile settings were correct then clicked " Apply".

I was then able to connect to the Telstra Mobile UTMS and access the internet successfully.

In order to check my usage, I went to [http://myprepaid.telstra.com](http://myprepaid.telstra.com), and clicked on "My Balance".

---

### Post by alexfish on 2011-02-03
> **jdcrownover said:**
> Wow, looonnnngggg post.  A prime example of why I have NOT yet made Ubuntu my primary operating system -- there is NO SINGLE GOOD INSTALL APPLICATION available.

I've been looking around trying to figure out how to get my Options Velocity modem working.  I see lots of suggestions with lots of packages, some of which I have install, but most of these require you to KNOW LINUX AT THE SYSTEM LEVEL to do anything.  THEY DON'T EVEN TELL YOU WHICH DIRECTORY YOU NEED TO PUT STUFF IN.

I read a post made in JANUARY 2010 about ZeroCD.  Here it is 11 months later, and there is STILL NOTHING IN THE UBUNTU UPDATES which allows my zeroCD to operate.

And I haven't even attempted yet to attach my peripheral devices to my Ubuntu laptop, mainly because I now expect the same LACK OF SUPPORT for them as well.

PS - I'm writing this from my WINDOWS 7 laptop, where my Options Velocity modem INSTALL WITH NO PROBLEMS AT ALL.
Remember one thing . Your service provider had these drivers pre-install on the device, and certainly for your choice of operating system,
most do not have Linux drivers pre-installed.

Perhaps the comments would be of a different nature,
If you had the will and the want to use Linux as an Operating system

---

### Post by wsoelivan on 2011-02-18
> 
**[B]For CDMA :Check to see if the ACM drivers will load for the device**:[/B]
**```
sudo modprobe cdc-acm
```[B]............................................................................**[/B]
**For other drivers examine files**
**lib/modules/kernel version/kernel/drivers/usb/serial**
**lib/modules/kernel version/kernel/drivers/usb/class**
**lib/modules/kernel version /kernel/drivers/net/usb**
**[B]............................................................................**[/B]
 
**[B]Alternately** a modprobe usbserial may load the generic serial drivers , the generic drivers are usually ok to get a connection working ,but may not provide full functionality of the modem[/B]
 
**" sudo modprobe usbserial vendor=0x[COLOR=blue]ID[/COLOR] product=0x[COLOR=blue]ID[/COLOR] "**
 
 
Alexfish,
 
I'm using Ubuntu Netbook 10.10, and using EVDO connection with Olive VME110 modem. Firstly I was trying to connect using wvdial command but didn't have much luck with it. Then now I am able to connect to the internet using the network manager (mobile broadband setup). However, I have a problem like you stated, in which it does not provide full functionality of the modem.
 
I'm supposed to have 3.1 Mbps downlink (on Windows, I managed to get 200+ KBps), while on Linux my speed is maxxed out at 55-60 Kbps (500ish Kbps). I believe the problem is because of the generic usb driver.
 
Since I'm new to Linux, could you please elaborate and shed some light on how I could get normal speed?
 
Fyi, I skipped this bit:
> 
**For CDMA :Check to see if the ACM drivers will load for the device**:
```
sudo modprobe cdc-acm
```**............................................................................**
For other drivers examine files
lib/modules/kernel version/kernel/drivers/usb/serial
lib/modules/kernel version/kernel/drivers/usb/class
lib/modules/kernel version /kernel/drivers/net/usb
**............................................................................**
 
Thank you.

---

### Post by alexfish on 2011-02-22
> **wsoelivan said:**
> Alexfish,
 
I'm using Ubuntu Netbook 10.10, and using EVDO connection with Olive VME110 modem. Firstly I was trying to connect using wvdial command but didn't have much luck with it. Then now I am able to connect to the internet using the network manager (mobile broadband setup). However, I have a problem like you stated, in which it does not provide full functionality of the modem.
 
I'm supposed to have 3.1 Mbps downlink (on Windows, I managed to get 200+ KBps), while on Linux my speed is maxxed out at 55-60 Kbps (500ish Kbps). I believe the problem is because of the generic usb driver.
 
Since I'm new to Linux, could you please elaborate and shed some light on how I could get normal speed?
 
Fyi, I skipped this bit:

 
Thank you.

Hi wsoeivan

and welcome to the forums

There is very little which can be achieved as Regards speed with Network Manager, other than setting the Type
IE: 3g , 2g, or selecting  preferred options , have you tried

Have you try ppp direct , where the buad rates can be selected

can also mention details of problem with wvdial ,

if modem-manager (network manager dependency) does not have a plugin for the device then
wvdial is usually the preferred method of connecting CDMA modems , esp where specific init codes can to be sent to the modem

can also post the dial up details from the Network Manager

---

### Post by pedrogfrancisco on 2011-02-25
ZTE k3805-z USB pen works with wvdial, as long as one uses wvdialconf before the first run and uses *99***1# as the phone number (you may have also to add "Stupid mode = 1" to wvdial.conf).

---

### Post by alexfish on 2011-02-26
hi pedrogfrancisco

The k3805-z has a icera chipset , and may need special init codes and udev rules to enable the device to use the cdc_ether connection, if using wvdial can check which interface is been used with "ifconfig" command

if only showing as standard ppp connection , then possible to point you in a direction, as to which sofware may work with this device, to enable use of cdc_ether connect

if have read first post as regards New Devices , using the "usb-devices" or "lsusb -t" or "lsusb -v" may show if it has a cdc_ether interface

regards

alexfish

---

### Post by pedrogfrancisco on 2011-03-29
It works on Ubuntu 11.04 :)
To anyone else reading this:
The two times I tried it didn't work the first time, connect a second and third time before giving up. Also, doing ifconfig usb0 -arp may or may not help, didn't experiment enough times.

---

### Post by alexfish on 2011-07-11
**Natty users**:** Betavine:   BCM connection manager** ( Vodafone devices)

BCM failing to initialize ;

test BCM from the terminal,
```
bcm 
```if you get the following error message
> Traceback (most recent call last):
  File "/usr/bin/bcm", line 10, in <module>
    from wader.common.utils import save_file, get_file_data
ImportError: No module named wader.common.utils
you will need to create a symlink for python 2.6 to 2.7 (wader)
```
sudo ln -s /usr/local/lib/python2.6/dist-packages/wader /usr/local/lib/python2.7/dist-packages/wader
```of note the dbus spec is not same

this is the diff between the existing BCM and the modem-manager
```
--- /etc/dbus-1/system.d/org.freedesktop.ModemManager.conf    2011-06-07 16:09:55.799695594 +0100
+++ /etc/dbus-1/system.d/org.freedesktop.ModemManager.conf.dpkg-new    2011-04-11 00:09:10.000000000 +0100
@@ -5,12 +5,10 @@
   <!-- This config allows anyone to control ModemManager -->
 
   <policy context="default">
-    <allow own="org.freedesktop.ModemManager.Modem.Gsm.SMS"/>
     <allow send_destination="org.freedesktop.ModemManager"/>
   </policy>
 
   <policy user="root">
-    <allow own="org.freedesktop.ModemManager.Modem.Gsm.SMS"/>
     <allow own="org.freedesktop.ModemManager"/>
   </policy>
```to view the bits check before install and after ;; save a coppy , of each it may save you a headache , if know how to use it
```
cat /etc/dbus-1/system.d/org.freedesktop.ModemManager.conf
```

RE: Wader-core , now available as for (Precise Pangolin), if have Next Generation Huawei device , possibly look to Huawie Mobile Partner  first .  RE foot of post   #[**60**]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60")

alexfish

---

### Post by alexfish on 2011-08-14
**Part of Betavine Site  has show to be using invalild security certificate (14 Aug 2011) so have copied the data**

**Copy of Betavine Know Working devices**

**Huawei devices that work with bcm **


[LIST]
[*]Huawei B970
[*]Huawei E1550
[LIST]
[*]Note: the E1550 Sometimes requires prodding with [Sakis3g]("http://www.sakis3g.org/") to get it recognized (modeswitch, setup TTY, register network).
[/LIST]
[*]Huawei E160B
[*]Huawei E172
[*]Huawei E220
[*]Huawei E270
[*]Huawei E272
[*]Huawei E3735
[*]Huawei E510
[*]Huawei E620
[*]Huawei E630
[*]Huawei E660a
[*]Huawei E870
[*]Huawei EM730V
[*]Huawei EM770
[*]Huawei K2540
[*]Huawei K3520
[*]Huawei K3565
[*]Huawei K3565rev2
[*]Huawei K3715
[*]Huawei K3765
[*]Huawei K4505
[/LIST]
 ** Huawei Devices that do not work with bcm as of 2011-02-28**

 
[LIST]
[*]Huawei E153
[/LIST]
 ** ZTE**

 
[LIST]
[*]ZTE K2525
[*]ZTE K3520-Z
[*]ZTE K3565-Z
[*]ZTE K3570-Z
[*]ZTE K3571-Z
[*]ZTE K3765-Z
[*]ZTE K3805-Z
[*]ZTE K4505-Z
[*]ZTE MF651
[/LIST]
 ** Option**

 
[LIST]
[*] Option Colt
[*] Option E3730
[*] Option Fuji-Lite(PPPD)
[*] Option Etna(PPPD)
[*] Option Etna(NDIS)
[*] Option Globe Surfer Icon
[*] Option GT Fusion
[*] Option GT Fusion Quad-lite
[*] Option GTM378
[*] Option GTMAX36
[*] Option Icon
[*] Option K3760
[*] Option Nozomi(Needs update to gudev parsing)
[/LIST]
 ** Sierra Wireless**

 
[LIST]
[*]Sierrawireless 875
[*]Sierrawireless MC8755
[/LIST]
 ** Sony Ericsson**

 
[LIST]
[*]Sony Ericsson K610i
[*]Sony Ericsson K618i
[/LIST]
 ** Ericsson**

 
[LIST]
[*]Ericsson MD300
[*]Ericsson F3307
[*]Ericsson F3507g
[*]Ericsson F3607gw
[/LIST]
 ** Dell**

 
[LIST]
[*]Dell D5520
[*]Dell D5530
[*]Dell D5540
[/LIST]
 ** Novatel**

 
[LIST]
[*]Novatel U630(Needs update to gudev parsing)
[*]Novatel U740
[*]Novatel XU870
[*]Novatel X950
[*]Novatel MC950D
[*]Novatel MC990D
[*]Novatel MiFi2352
[/LIST]
 ** Nokia**

 
[LIST]
[*]Nokia 6230
[/LIST]

---

### Post by Linuxisfast on 2011-08-22
Thankfully all the major network in Philippines work right out of the box, in case of Smart, all one needs is to enter smartbro in APN, in case of SUN its fbband and viola, net works real good, only hitch in Philippines is upgrading the subscription as it needs a Windows based applet. For Postpaid, its not an issue.

---

### Post by jhock on 2011-09-28
Hi,

I went through the above processes and all was fine up to the command:

echo -e "AT+CPIN?\r" > /dev/ttyUSB2

This command gave me the error:

+CME ERROR: 10

When I run the command:

sudo sakis3g

I get the error:

Modem responded "ERROR" while checking for PIN.
 
Does this mean that I have locked my SIM?

When I put the SIM in a mobile phone the simPID works but the phone gives and error:

SIM card not valid

I thought that this might mean that the Telstra SIM card isn't registered to run on my phone which has a vodafone SIM. Something about having to unlock the vodafone SIM before changing to another SIM.

I am running on an ASUS eePC 10H:

 Ubuntu 11.04 - the Natty Narwhal
 Telstra Ultimate AirCard 312U Sierra Wireless USB modem

Can someone help me get my mobile broadband working?

Thanks.


John H.

---

### Post by alexfish on 2011-10-09
> **jhock said:**
> Hi,

I went through the above processes and all was fine up to the command:

echo -e "AT+CPIN?\r" > /dev/ttyUSB2

This command gave me the error:

+CME ERROR: 10

When I run the command:

sudo sakis3g

I get the error:

Modem responded "ERROR" while checking for PIN.
 
Does this mean that I have locked my SIM?

When I put the SIM in a mobile phone the simPID works but the phone gives and error:

SIM card not valid

I thought that this might mean that the Telstra SIM card isn't registered to run on my phone which has a vodafone SIM. Something about having to unlock the vodafone SIM before changing to another SIM.

I am running on an ASUS eePC 10H:

 Ubuntu 11.04 - the Natty Narwhal
 Telstra Ultimate AirCard 312U Sierra Wireless USB modem

Can someone help me get my mobile broadband working?

Thanks.


John H.

for error codes can look here
[http://www.smssolutions.net/tutorials/gsm/gsmerrorcodes/](http://www.smssolutions.net/tutorials/gsm/gsmerrorcodes/)

if  having incompatible problems  with equipment then look to your isp or supplier, 
regards

alexfish

---

### Post by alexfish on 2011-11-10
**RE 11.04  may apply to 11.10**

**Note:**

Do not install usb_modeswitch from debian ;if have upgraded and and wondered why the device no longer works : 
Answer usb_modeswitch debian may have a different dispatcher

Device not switching

try connect at boot and also after boot

Still not switching try the Disk Utility . 
if the device list as sr* the chances are it may switch by using the the eject command

check for changes in the usb IDs with the lsusb command from the terminal

If the device has change IDs then it indicates switching

List the new ids with the lsusb Command " lsusb -t -d ****:**** " : edit the ****:**** for the device

IE: 
```
lsusb -t -d 19d2:0031
```Example output
```
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/10p, 12M
    |__ Port 1: Dev 2, If 0, Class=HID, Driver=usbhid, 1.5M
    |__ Port 1: Dev 2, If 1, Class=HID, Driver=usbhid, 1.5M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/10p, 480M
    |__ Port 2: Dev 3, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 8: Dev 30, If 0, Class=vend., Driver=option, 480M
    |__ Port 8: Dev 30, If 1, Class=vend., Driver=option, 480M
    |__ Port 8: Dev 30, If 2, Class=stor., Driver=usb-storage, 480M
    |__ Port 8: Dev 30, If 3, Class=vend., Driver=option, 480M
```the above shows the device has configured and drivers are bound to the device

if most of the above shows 
Driver=,****
then the device has not fully configured

can check by 
```
ls -al /dev/serial/by-id/*
```this should show the device and the ports it is connected to

Example 
```
/dev/serial/by-id/usb-ZTE_Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
/dev/serial/by-id/usb-ZTE_Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
/dev/serial/by-id/usb-ZTE_Incorporated_ZTE_CDMA_Technologies_MSM_1234567890ABCDEF-if03-port0 -> ../../ttyUSB2
```if an err = cannot access /dev/serial/by-id/$: No such file or directory . then the device has not configured


No driver loading then best try sakis3g , use the sakis3g setup option , it may find a suitable driver and load it.

Device still not recognized

see if your device is supported on Ubuntu
```
tar tf /usr/share/usb_modeswitch/configPack.tar.gz
```this will list the device database , if the device is listed and not switching then there is a problem

follow this change the device id highlighted in [COLOR=Blue]blue[/COLOR] for the device
```
sudo su

cd /etc/usb_modeswitch.d

tar -x [COLOR=Blue]19d2:2000[/COLOR] -f /usr/share/usb_modeswitch/configPack.tar.gz

 usb_modeswitch -W -c /etc/usb_modeswitch.d/[COLOR=Blue]19d2:2000[/COLOR]

```note if there are any changes
: 
Not switching report bugs to Ubuntu
Device not listed : Please refer to usb_modeswitch for guidance
Drivers not loading try sakis3g if may find a suitable driver : if this fails assume device is not supported at present ,or report bugs to Ubuntu

How to check driver modules remember to change the device ID's in [COLOR=Blue]blue[/COLOR]
search the current kernel : all letters must be in upper case
EXAMPLE
```
grep -i v[COLOR=Blue]12D1[/COLOR]p[COLOR=Blue]1436 [/COLOR]/lib/modules/`uname -r`/modules.alias
```search all kernels
```
grep -i v[COLOR=Blue]12D1[/COLOR]p[COLOR=Blue]1436[/COLOR] /lib/modules/*/modules.alias
```Example output from current kernel
```
alexfish@alexfish-desktop:~$ grep -i v12D1p1436 /lib/modules/`uname -r`/modules.alias
alias usb:v12D1p1436d0000dc*dsc*dp*ic*isc*ip* usb_storage
alias usb:v12D1p1436d*dc*dsc*dp*icFFiscFFipFF* [COLOR=Red]option[/COLOR]
``` red bit = driver[COLOR=Red] module[/COLOR]
Note This: from the above have place *'s at the appropriate
could be a pointer to device which does not change Ids , or could be  problematic , if a problem can try sakis3g with the no storage option
look through your log files if the device is disconnecting and reconnecting:: link to sakis3g forum ,  								 									**[Re: tty_send_command]("http://forum.sakis3g.org/smf/index.php?topic=99.msg509#msg509") 									**

```
alias usb:v12D1p1436d0000dc*dsc*dp*ic**isc**ip* usb_storage
alias usb:v12D1p1436d****dc*dsc*dp*icFFiscFFipFF* option
```if the device lists and the module is not loading
```
sudo modprobe <[COLOR=Red]driver[/COLOR]>
```**Note:** all new usb_modeswitch device switching data should be placed in the /etc/usb_modeswitch.d folder

If have upgraded to Debian Packages and the device is not switching then it could be the usb_modeswitch dispatcher

Reinstall the Ubuntu version of usb_modeswtch + the data

if can't role back the version and have saved a copy of the original dispatcher try
```
gksu nautilus
```go to the usb_modeswitch_dispatcher(copy)  : ensure named "usb_modeswitch_dispatcher" copy it

goto the /usr/sbin/

remove the usb_modeswitch_dispatcher exec (recognized as a diamond) to the rubbish bin

paste the usb_modeswitch_dispatcher(copy)

ensure it is named  "usb_modeswitch_dispatcher"

exit the terminal , plug the device in and see what happens

**ALSO CHECK OUT POST****S **#[**60 **]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60")and  #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61")

---

### Post by alexfish on 2011-11-10
**First Read Foot of page, RE: **[B]IMPORTANT NOTIFICATION . prior to committing. 

Also worth downloading if at this Post: [/B][*Linux* USB *drivers*]("http://www.google.com/url?sa=t&rct=j&q=12m%20driver%20linux&source=web&cd=4&ved=0CDoQFjAD&url=http%3A%2F%2Ffree-electrons.com%2Fdoc%2Flinux-usb.pdf&ei=eLttT__zCMm5hAeIw-iOBw&usg=AFQjCNF5eq4d2jdJPzw6Zj-HNlB8xPY15A&cad=rja")   **[B]: Related post **[/B]  			#[**68**]("http://ubuntuforums.org/showpost.php?p=11766536&postcount=68")
[B][B] 
how to find a suitable module[/B]: try this
[/B]```
grep usb /sys/bus/usb/devices/*/modalias
```look through the list to identify the device
example
```
alexfish@alexfish-desktop:~$ grep usb /sys/bus/usb/devices/*/modalias
/sys/bus/usb/devices/1-0:1.0/modalias:usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/1-2:1.0/modalias:usb:v059Bp047Ad0000dc00dsc00dp00ic08isc06ip50
/sys/bus/usb/devices/1-8:1.0/modalias:usb:v[COLOR=Blue]19D2p0031[/COLOR]d0000dc00dsc00dp00icFFiscFF[COLOR=Blue]ipFF[/COLOR]
/sys/bus/usb/devices/1-8:1.1/modalias:usb:[COLOR=Blue]v19D2p0031[/COLOR]d0000dc00dsc00dp00icFFiscFF[COLOR=Blue]ipFF[/COLOR]
/sys/bus/usb/devices/1-8:1.2/modalias:usb:[COLOR=Blue]v19D2p0031[/COLOR]d0000dc00dsc00dp00ic08isc06[COLOR=Blue]ip50[/COLOR]
/sys/bus/usb/devices/1-8:1.3/modalias:usb[COLOR=Blue]:v19D2p0031[/COLOR]d0000dc00dsc00dp00icFFiscFF[COLOR=Blue]ipFF[/COLOR]
/sys/bus/usb/devices/2-0:1.0/modalias:usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/2-1:1.0/modalias:usb:v0603p00F2d0112dc00dsc00dp00ic03isc01ip01
/sys/bus/usb/devices/2-1:1.1/modalias:usb:v0603p00F2d0112dc00dsc00dp00ic03isc00ip00

```take the last 4 bits of the modalias of each line of the device and check all
from example
```
/sys/bus/usb/devices/1-8:1.3/modalias:usb:v19D2p0031d0000dc00dsc00dp00icFFiscFFipFF
``` : use "[COLOR=Blue]ipFF[/COLOR]"

find a suitable driver
say  for instance
normal usb devices like cdma and option drivers
```
grep -i [COLOR=Blue]ipFF[/COLOR] /lib/modules/`uname -r`/modules.alias
```fast interface devices
```
grep -i [COLOR=Blue]ip00[/COLOR] /lib/modules/`uname -r`/modules.alias
```look through the list,

**Example of List** (part of)
```
alias usb:v12D1p1401d*dc*dsc*dp*icFFiscFFipFF* option
alias usb:v12D1p1004d*dc*dsc*dp*icFFiscFFipFF* option
alias usb:v12D1p1003d*dc*dsc*dp*icFFiscFFipFF* option
alias usb:v12D1p1001d*dc*dsc*dp*icFFiscFFipFF* option
alias usb:v106Cp3718d*dc*dsc*dp*icFFiscFFipFF* qcaux
alias usb:v1199p6892d*dc*dsc*dp*icFFiscFFipFF* sierra
[COLOR=Blue]alias usb:v1199p6891d*dc*dsc*dp*icFFiscFFipFF* sierra[/COLOR]
alias usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF* sierra
```check your device modalias listing IE:
```
[COLOR=Blue]usb:v19D2p0031d0000dc00dsc00dp00icFFiscFFipFF[/COLOR]
```  copy and paste the device modalias + a line from the grep modules ;
Now use * to line up the two modalias :: look at the pattern 
Example 
```
usb:v19D2p0031d0000dc00dsc00dp00icFFiscFFipFF
usb:v1199p6891d****dc**dsc**dp**icFFiscFFipFF* sierra
``` if the driver looks promising ; load the driver. use the modprobe [COLOR=Blue]<module>[/COLOR]
example 
]```
sudo su
modprobe [COLOR=Blue]sierra[/COLOR]
```check the system to see if a file new-id ; usualy in the path /sys/bus/drivers/<module name>/new_id
```
ls /sys/bus/usb/drivers/*/module/drivers/*/new_id
```this gives the path
```
/sys/bus/usb/drivers/sierra/module/drivers/usb-serial:sierra/new_id
```**Huawie Mobile Partner** (Drivers) if you have installed the drivers then if **connected  via usb port** , the net part shows as
```
/sys/bus/usb/drivers/huawei_ether/module/drivers/usb:huawei_ether/new_id
``` The Actual Driver is " hw_cdc_driver" try "modinfo hw_cdc_driver" to see details.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is a example of a device which normally uses the option driver 
to force the driver example change the ID's of the device highlighted in[COLOR=Blue] blue[/COLOR] : Also not the change from upper case to lower case
```
sudo su
 echo "[COLOR=Blue]19d2 0031[/COLOR]" > /sys/bus/usb/drivers/sierra/module/drivers/usb-serial:sierra/new_id
```check the results in the /dev/tty or the dev/serial
```
ls -al /dev/serial/by-id/*
```also list  usb devices with this code
```
usb-devices
```To List the modules by vendor remember to change the id in [COLOR=Blue]blue[/COLOR], and note the lower case if lsusb listing is "19D2 then = [COLOR=Blue]19d2[/COLOR]"
```
grep -i [COLOR=Blue]v19d2[/COLOR] /lib/modules/`uname -r`/modules.alias
```[B]
USB ID's:
don,t forget to keep the usb ids up to date
to view the usb.ids paste this in the browser
[/B]```
file:///var/lib/usbutils/usb.ids
``` or can wget daily snapshot

```
wget http://www.linux-usb.org/usb.ids
``` file will be in the home directory , open with your browser
 the info  may indicate the type of driver required for the device :IE wimax ,gobi etc etc not always specific , but usually confirmed by the modalias
to update the usb.ids
```
sudo /usr/sbin/update-usbids
```[B]Remember before going out to buy the Latest gadget check the device ID's : a little research helps
[/B]Here I am assuming you Are connected by one means or another. if the info not available , It is your decision[B] 


Finally :[/B] check out  #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61")

[B]If have a device and found a suitable driver using the above Please report at Launch Pad :also feel free to post Here
Device description : Device USB-IDs : Driver Module : The Path to the new_id :: IE: echo "[COLOR=Blue]19d2 0031[/COLOR]" >[COLOR=Blue] /sys/bus/usb/drivers/sierra/module/drivers/usb-serial:sierra/new_id[/COLOR]" 
OR  how it was achieved [/B]

A driver to play about with , try safe-serial use at own risk
use grep to find devices which can be used
```
grep -i 02ip /lib/modules/`uname -r`/modules.alias
``` below is the modinfo of the driver
```
:~$ modinfo safe-serial
filename:       /lib/modules/2.6.38-12-generic/kernel/drivers/usb/serial/safe_serial.ko
license:        GPL
description:    USB Safe Encapsulated Serial
author:         sl@lineo.com, tbr@lineo.com, Johan Hovold <jhovold@gmail.com>
srcversion:     7F505336AEAE3A308E5D19D
alias:          usb:v0000p0000d*dc02dsc*dp*icFFisc02ip*
alias:          usb:v05F9pFFFFd*dc02dsc*dp*icFFisc02ip*
alias:          usb:v04DDp8004d*dc02dsc*dp*icFFisc02ip*
alias:          usb:v04DDp8003d*dc02dsc*dp*icFFisc02ip*
alias:          usb:v04DDp8002d*dc02dsc*dp*icFFisc02ip*
alias:          usb:v04DDp8001d*dc02dsc*dp*icFFisc02ip*
alias:          usb:v03F0p2101d*dc02dsc*dp*icFFisc02ip*
alias:          usb:v049FpFFFFd*dc02dsc*dp*icFFisc02ip*
depends:        usbserial
vermagic:       2.6.38-12-generic SMP mod_unload modversions 686 
parm:           vendor:User specified USB idVendor (required) (ushort)
parm:           product:User specified USB idProduct (required) (ushort)
parm:           debug:Debug enabled or not (bool)
parm:           safe:Turn Safe Encapsulation On/Off (bool)
parm:           padded:Pad to full wMaxPacketSize On/Off (bool)
```Question What is the deference between searching a hard link and a sym link
Answer: if your looking to install a driver at connection there is less to look at See Below
also **note the base driver: Example** also reason to highlight in [COLOR=Blue]BLUE[/COLOR]
> /sys/bus/usb-serial/drivers/generic/new_id < This one , say if the option 1 driver will not Bind to the device or Problematic then look to use the  base driver example at Post #2 shows the original method to bind to the id's at boot
/sys/bus/usb-serial/drivers/option1/new_id```
1./sys/bus/usb/drivers/option/module/drivers/usb-serial:option1/new_id
2 . /sys/bus/usb-serial/drivers/option1/new_id

1) ls /sys/bus/usb/drivers/*/module/drivers/*/new_id

/sys/bus/usb/drivers/hub/module/drivers/usb:hub/new_id
/sys/bus/usb/drivers/hub/module/drivers/usb:usbfs/new_id
[COLOR=Blue]/sys/bus/usb/drivers/option/module/drivers/usb-serial:option1/new_id[/COLOR]
/sys/bus/usb/drivers/uas/module/drivers/usb:uas/new_id
/sys/bus/usb/drivers/usbfs/module/drivers/usb:hub/new_id
/sys/bus/usb/drivers/usbfs/module/drivers/usb:usbfs/new_id
/sys/bus/usb/drivers/usbhid/module/drivers/hid:generic-usb/new_id
/sys/bus/usb/drivers/usbhid/module/drivers/usb:usbhid/new_id
/sys/bus/usb/drivers/usbserial_generic/module/drivers/usb-serial:generic/new_id
/sys/bus/usb/drivers/usbserial/module/drivers/usb-serial:generic/new_id
/sys/bus/usb/drivers/usb-storage/module/drivers/usb:usb-storage/new_id

2) ls /sys/bus/*/drivers/*/new_id

/sys/bus/hid/drivers/generic-usb/new_id
/sys/bus/pci/drivers/agpgart-amdk7/new_id
/sys/bus/pci/drivers/agpgart-intel/new_id
/sys/bus/pci/drivers/agpgart-nvidia/new_id
/sys/bus/pci/drivers/agpgart-via/new_id
/sys/bus/pci/drivers/asiliantfb/new_id
/sys/bus/pci/drivers/ata_generic/new_id
/sys/bus/pci/drivers/ata_piix/new_id
/sys/bus/pci/drivers/ce4100_spi/new_id
/sys/bus/pci/drivers/C-Media PCI/new_id
/sys/bus/pci/drivers/ehci_hcd/new_id
/sys/bus/pci/drivers/forcedeth/new_id
/sys/bus/pci/drivers/imsttfb/new_id
/sys/bus/pci/drivers/Intel ICH/new_id
/sys/bus/pci/drivers/ioapic/new_id
/sys/bus/pci/drivers/k8temp/new_id
/sys/bus/pci/drivers/langwell_gpio/new_id
/sys/bus/pci/drivers/nForce2_smbus/new_id
/sys/bus/pci/drivers/nvidia/new_id
/sys/bus/pci/drivers/ohci_hcd/new_id
/sys/bus/pci/drivers/parport_pc/new_id
/sys/bus/pci/drivers/pata_acpi/new_id
/sys/bus/pci/drivers/pata_amd/new_id
/sys/bus/pci/drivers/pata_sis/new_id
/sys/bus/pci/drivers/pci_eisa/new_id
/sys/bus/pci/drivers/pcieport/new_id
/sys/bus/pci/drivers/pdc_adma/new_id
/sys/bus/pci/drivers/sata_nv/new_id
/sys/bus/pci/drivers/serial/new_id
/sys/bus/pci/drivers/uhci_hcd/new_id
/sys/bus/usb/drivers/hub/new_id
/sys/bus/usb/drivers/uas/new_id
/sys/bus/usb/drivers/usbfs/new_id
/sys/bus/usb/drivers/usbhid/new_id
/sys/bus/usb/drivers/usb-storage/new_id
/sys/bus/usb-serial/drivers/generic/new_id
/sys/bus/usb-serial/drivers/option1/new_id
``` [**Has anyone got the Huawei E586 working on ubuntu 11.10?**]("http://ubuntuforums.org/showthread.php?t=1875315") 

worth following, but don't know if the outcome will be a success :
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[B]IMPORTANT NOTIFICATION 

[/B] **HUAWEI PRODUCT E585**** (12d1:1446**) :3g/4g **read**

**Example of devices with different switching modes**

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=836](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=836)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**also look at**   
**HUAWEI PRODUCT E353 (0x1506)** 
[http://www.kernel.org/pub/linux/kernel/v3.0/ChangeLog-3.1.6](http://www.kernel.org/pub/linux/kernel/v3.0/ChangeLog-3.1.6)

**definitely look here**
**[SOLVED]** [Huawei E5832 and Ubuntu 12.04]("http://ubuntuforums.org/showthread.php?t=1927519")

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

have check latest updates on Ubuntu 11.04 as regards this driver **cdc-wdm**
so if have Huawei device similar to the above check the Modalias , info for driver shows
```
alexfish@alexfish-desktop:~$ modinfo cdc-wdm
filename:       /lib/modules/2.6.38-13-generic/kernel/drivers/usb/class/cdc-wdm.ko
license:        GPL
description:    USB Abstract Control Model driver for USB WCM Device Management
author:         Oliver Neukum
srcversion:     CAFE8B3EA57870E596D4DA7
alias:          usb:v*p*d*dc*dsc*dp*ic02isc09ip*
depends:        
vermagic:       2.6.38-13-generic SMP mod_unload modversions 686

```You may have to load the driver , then put the device id's into the new id / path
```
/sys/bus/usb/drivers/cdc_wdm/module/drivers/usb:cdc_wdm/new_id
```According to info it only engages the cdc-ether type interface so will also have to bind the option or usb-serial driver after binding the cdc-wdm driver module
Note: part of the device Modalias should show[FONT=monospace]
[/FONT]```
usb:v*p*d*dc*dsc*dp*ic02isc09ip*
```[http://lists.openwall.net/netdev/2012/01/20/7](http://lists.openwall.net/netdev/2012/01/20/7)

Please read though the next few posts if have one of these devices 


alexfish

---

### Post by alexfish on 2011-11-15
**The script With reference to post: **      oPost  #**[2]("http://ubuntuforums.org/showpost.php?p=9201405&postcount=2")** 

Requires package TCL

The tcl package is not part of Ubuntu 11.10 . What can you do Look here  #[**30**]("http://ubuntuforums.org/showpost.php?p=11559852&postcount=30")  .. may be wise to keep a copy on usb stick

script name eject.tcl or what ever you want to call it. after saving the file in /home/file set the Execute bit in the properties
use from the terminal
./scriptname argv

Remember the eject command is useless if the device is configured use the argv "tty" to find device details

there are no traps in some parts of the script so ensure run from the terminal , it will just but out if error , but do not try to modify the script unless you know
how to catch errors

Usage: to find ejectable usb modem

suggest: "eject rule" or usb_modeswitch rule 
eject: "device" will list new ids if found "only if the SR changes to SD ; hint on this one if the device switches and the device has both SD* and SR* and is unstable
can try and safely remove the SR bit check with the Disk Utility
 
check: "tty* exits" in dev/serial/by-id + list all possible udev rules

list: the usb_modeswitch device database

connect the device and only 1 device , wait a few moments to all the system to settle

follow these commands , Remember to change the "[COLOR=Blue]./script[/COLOR]" to your script [COLOR=Blue]name[/COLOR]

List the device ; the script may crash at this point if already switched , or if the system not settled , have kept the script short as possible by ommitting traps
```
[COLOR=Blue]./scrip[/COLOR]t eject sr
```List possible eject rule and usb_modeswitch rule > Please refer the usb_modswitch forum if device not switching or read Posts       #**[60]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60")   and #****[59]("http://ubuntuforums.org/showpost.php?p=11443633&postcount=59")** 
```
[COLOR=Blue]./script [/COLOR]eject sr 1
```Try to eject the device and search for any changes in the SD* ID's if found just look at the list if happy
try to list the device tty*
```
[COLOR=Blue]./script[/COLOR] eject sr 2 
```search /dev/serial/by-id/* 
Check the tty status and AT command response + list the rules available to udev , may help to write your own rules
```
[COLOR=Blue]./script [/COLOR]tty
```the tty command is usefull if find the likes of wvdial and ppp gammu cant find the port ,,IE the device may show different tty* make your own rules to suit , RE: post                             Post  #**[2]("http://ubuntuforums.org/showpost.php?p=9201405&postcount=2")** 

List usb_modeswitch database on 11.04 and possible 11.10
```
[COLOR=Blue]./script[/COLOR] database
```if the device is in the database and not switching see post                             #**[60]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60") **

After running the argv tty, take time to look through all the data of udev and also note the modem status and the response to AT command: it may help to find what a particular port is for.

ADDED:** TIP**: look at
```
 ATTRS{bNumEndpoints}=="*"
  ATTRS{bInterfaceClass}=="*"
  ATTRS{bInterfaceSubClass}=="*"
  ATTRS{bInterfaceProtocol}=="*"
``````
#!/bin/sh
# the next line restarts using tclsh \
exec tclsh "$0" "$@"
##################################################
# Some of vars are not what they seem esp $tty.

proc udevadm-tty {bit} {
    if { [catch {set udevadm_tty [exec udevadm info -a path -n /dev/$bit]} fid] } {
        puts $fid
        return
    } else {
        puts "$udevadm_tty\n"
        }
        unset udevadm_tty
    return
}
###########################################################################
proc ttys {} {
set dolist 1
    if { [catch {set List [exec ls -l /dev/serial/by-id]} fid] } {
        puts "$fid\n"
        return
    } else {
        puts "/dev/serial/by-id:\n\n$List\n"
        }
    #########################
    # parse device : ttys
    if {$dolist == 1} {
        set len [llength $List]
    foreach bit $List {
        set usb [string first {usb} $bit]
            if {$usb > -1} {
                puts "--------- Udevadm device info-------\n\n"
                puts "--$bit: "
            }

        set tty [string first {tty} $bit]
            if {$tty > -1} {
            set bit [string range $bit $tty end]
            set udevtty "/dev/$bit"
            #puts "$udevtty\n"
#TODO  get the serial info here
    tty_status $udevtty
##########################
            udevadm-tty $bit

            }
    }
 }
}
###########################
 proc tty_status {tty} {
    set tty [string trim $tty]
    set isdev [string first /dev/tty $tty]
        if {$isdev  > -1} {set tty $tty}
        if {$isdev == -1} {set tty "/dev/$tty"}    
    if { [catch {set serial [open $tty RDWR]} fid] } {
           puts  "\n$tty : $fid \n"
        return
    } else {
    ##################################################
    # set the port to stnd 115200 buffering DTR 1
    ##################################################
    fconfigure $serial -mode "115200,n,8,1"
    fconfigure $serial -blocking 0 -buffering full -ttycontrol {RTS 0 DTR 1}
    after 500
    set data [fconfigure $serial -ttystatus]
    puts "$tty : Status : $data"
        puts $serial "AT"
        after 100
        flush $serial
        after 100
        set data6 [read $serial]
        puts "AT$data6"
    
    close $serial}
return
}
#################################################
proc udevadm-sr {bit  bNumInterfaces ejects} {
set bit "/dev/$bit"  
    if { [catch {set udevadm_sr [exec udevadm info -a path -n $bit]} fid] } {
        puts $fid
        return
    } else {
        set idvendor "ATTRS{idVendor}=="
        set idproduct "ATTRS{idProduct}=="
        set manufacturer "ATTRS{manufacturer}=="
        set cmds [split $udevadm_sr "\n"]
        foreach cmd $cmds {
            set cmd [string trim $cmd]
######################################################
        set check [string first $manufacturer $cmd]
            if {$check > -1} {
             set global manufacturers
                set manufacturers $cmd
               puts $manufacturers
                puts ""
            global usb_ids
            set usb_ids $usb_id
    
            return $usb_ids
            }
######################################################
        set vendor [string first $idvendor $cmd]
            if {$vendor > -1} {
             set global vendors
                set vendors $cmd
                set cut {"}
                set idvend [split $vendors $cut]
                    set idvend [lindex $idvend 1]
            }
#####################################################
        set product [string first $idproduct $cmd]
            if {$product > -1} {
             set global products
                set global usbid
                set products $cmd
                set cut {"}
                set idprod [split $products $cut]
                set idprod [lindex $idprod 1]
                #puts $idprod
##################################################SET THE REAL USB ID
                set global usb_id
                set usb_id "$idvend:$idprod"
                puts $usb_id                
##################################################
                set usbid "$vendors,$products"
                puts "Device: $usb_id"
                if {$ejects == 1} {
                puts "Trap2 $usb_id"
                lsusb_driver $usb_id
                set ejectrule  {RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"}
                set ejectrule "$usbid,$ejectrule"
                puts "eject rule :"
                puts "$ejectrule\n"
#TODO  SORT THE VARS IE MODESWITCH RULE ETC THESE ARE HASHED OUT
                set global modeswitchrule
                set modeswitchrule {RUN+="usb_modeswitch '%b/%k'"}
                set modeswitchrule "$usbid,$modeswitchrule"
                puts "usb_modeswitch.d rule :" 
                puts "$modeswitchrule\n"
#TODO NOTE this should be in latest version of usb_modeswith
#set optiondriverbind {ATTR{bInterfaceClass}=="ff", ATTR{bInterfaceNumber}=="00", ATTRS{bNumConfigurations}=="*", RUN+="usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}"}
                }
            }
####################################################
            set ejectmsg "not ejectable"
            if {$bNumInterfaces == $cmd} {
                puts "ejectable or remove device $bit"
                if {$ejects == 1} {
                }

                if {$ejects == 2} {

                set eject [exec udisks --eject $bit]
                puts "device $bit ejected"
                }
               # This function disabled but can use the Disk Utility to safely unmount  part of a unstable device 
               # if {$ejects == 3} {

               # set eject [exec udisks --unmount $bit]
               # puts "unmount: $bit "
               # }
################ now check for the device ID  change and changes in configs could be sd* *=alphabetical
            }                
        }

        }
        unset udevadm_sr
    return
}
proc eject_sr { find ejects } {
# set all the rules to look for
#TODO not all is used in this version
set bNumInterfaces "ATTRS{bNumInterfaces}=="
set idvendor "ATTRS{idVendor}=="
set idproduct "ATTRS{idProduct}=="
set bnum {" 1"}
set bNumInterfaces "$bNumInterfaces$bnum"
set dolist 1
    if { [catch {set List [exec ls -l /dev/disk/by-id]} fid] } {
        puts "$fid\n"
        return
    } else {
        }
    #########################
    # parse device : sr* or sd*
    if {$dolist == 1} {
        set len [llength $List]
    foreach bit $List {
        set usb [string first {usb} $bit]
            if {$usb > -1} {
            }
################## need argv at first line #################### sr* or sd*
        set srbit [string first $find $bit]
            if {$srbit > -1} {
            set bit [string range $bit $srbit end]
            set udevsrbit "/dev/$bit"
            udevadm-sr $bit $bNumInterfaces $ejects
            }
    }
  }
}
#################################################

proc lsusb_driver {usb_ids} {
  if { [catch {set List [exec lsusb -t -d $usb_ids ]} fid] } {
        puts "Device: $usb_ids :ERR :Driver missing\n"
        set List $fid
        set t 0
        set found 0
        foreach inlist $List {
            incr t
           set check [string first "If" $inlist]
            if {$check > -1} {
            set inlist [string trim $inlist ","]
            set found 1
            }
            if {$found == 1} {
            set check [string first "Driver" $inlist]
            if {$check > -1} {
            set inlist [string trim $inlist ","]
            if {$inlist == "Driver="} {
                puts "$inlist None"
                } else {
                    puts $inlist
                    }
            }
           }
         }

        return
    } else {
        set t 0
        set found 0
        foreach inlist $List {
            incr t
           set check [string first "If" $inlist]
            if {$check > -1} {
            set inlist [string trim $inlist ","]
            set found 1
            }
            if {$found == 1} {

           set check [string first "Driver" $inlist]
            if {$check > -1} {
            set inlist [string trim $inlist ","]
            puts $inlist
            }
            }
        }
        }
return
}
proc database {} {
set List [exec tar ft /usr/share/usb_modeswitch/configPack.tar.gz]
puts $List
}
####################################################
#MAIN
###################################################
set buff [lindex $argv 0]
if {$buff == "eject"} {
        set find [lindex $argv 1]
        set ejects [lindex $argv 2]
       # puts $ejects
        eject_sr  $find $ejects
        puts $usb_ids
        if {$ejects == 2} {
            set ejects ""
            set find "sd"
            after 10000
            eject_sr  $find $ejects
            puts "Wait"
            after 3000
            lsusb_driver $usb_ids
        }
    }

if {$buff == "database"} {
        database        
    }
if {$buff == "tty"} {
        ttys    
    }
#END
```The device Not Switching  from The eject command ,+ device not in the  Usb_Modeswitch  data base , Obvious , Visit USB MODESWITCH FORUM

If have a device with Net interface IE ;
The driver shows up as something like cdc-ether then can use a rule to bring up the interface , find by looking through the data of the argv "tty" ; remember to change the [COLOR=Blue]*****[/COLOR] for your device id's
look at posts                                    #**[59]("http://ubuntuforums.org/showpost.php?p=11443633&postcount=59")  and #[60]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60")**  then come back + Continue Reading the rest of this thead , 
Yes I know this Thread is Long , But EACH device is different
 

```
ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="[COLOR=Blue]****[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]****[/COLOR]", RUN="/sbin/ifconfig %k -arp"
```Example:
> ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="[COLOR=Blue]19d2[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]1003[/COLOR]", RUN="/sbin/ifconfig %k -arp"Here is a link to Linux Cross Reference : it will take to usb net drivers . its worth looking at ; Notice the Kernel version : 
[http://lxr.linux.no/#linux+v2.6.38/drivers/net/usb](http://lxr.linux.no/#linux+v2.6.38/drivers/net/usb)

for other drivers
[serial]("http://lxr.linux.no/linux+*/drivers/usb/serial/")
[class]("http://lxr.linux.no/linux+*/drivers/usb/class/")

need to know kernel version can look in the outputs of the "[COLOR=Blue]./script [/COLOR]tty"
or
```
uname -a
```ADDED FOR FUN:

if wondering why your at this POST

these devices are [http://www.thefreedictionary.com/ad+infinitum](http://www.thefreedictionary.com/ad+infinitum)

best do that link with Ubuntu or ANY other Linux Distro

---

### Post by alexfish on 2012-01-04
**MM-Dbus-Test**:

A bash script using the dbus-send to communicate with modem-manager
similar to the mm-test.py (yes I know python is easier) who said that

**What is different about this script :**
if  3g device, mayshould show MCC and MNC codes , (read through post #1) , if CDMA may reveal SID , 
 so can look up the serviceproviders data base  (read through post #1)

should also show which method is used to connect IE: (PPP , DHCP , Static )

**Dependencies :**"**dbus-send**"  : "**modem-manager**" , check to see if on system but should work with latest Ubuntu supported distro's.

**ADDED:** if have configuration problems, : IE the modem-manager hanging onto the device or device hanging after a disconnection, initially this script tests for a device enabled status at start ,
 when a status of device enabled = true , the script will request a disable false ; then request enable true ; result = enabled , end of script does enabled false, the device should then connect with NM.
The script will also indicate if enable flag {fail}: This is shown sequentially at the beginning of the outputs , and at the end of the outputs.
If modem-manager is failing to detect the device or can't do the enable flag , test the device with the script given at post #61, using the arg TTY, if detected . report  bugs to launch pad.

Where is the best place for the script
Suggest home directory
Save the file as "**mm-dbus-test**" or other.
Once Saved.
Right click on the file and check the Properties , Permissions , and check the Execute.
Call from the terminal
```
./mm-dbus-test
``````
#!/bin/bash

########################################################################
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by 
# the Free Software Foundation; either version 2 of the License, or   
# (at your option) any later version.                                  
#                                                                      
# This program is distributed in the hope that it will be useful,      
# but WITHOUT ANY WARRANTY; without even the implied warranty of      
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the        
# GNU General Public License for more details:                        
########################################################################
# cisabfone-MM-Dbus-Test (0.1.b)                                      
#  (0.1.b) added CDMA support (untested)                                  
# Copywrite (C) cisabfone@gmail.com                                       
# BUGS and ALL : ah.cisab@gmail.com                                       
########################################################################

INTERFACE_PROPERTIES="org.freedesktop.DBus.Properties"
MM_DBUS_SERVICE="org.freedesktop.ModemManager"
DBUS_PATH="/org/freedesktop/ModemManager"
DBUS_INTERFACE="org.freedesktop.ModemManager"
MODEM="org.freedesktop.ModemManager.Modem"
MODEM_CDMA="org.freedesktop.ModemManager.Modem.Cdma"
GSM_CARD="org.freedesktop.ModemManager.Modem.Gsm.Card"
GSM_NETWORK="org.freedesktop.ModemManager.Modem.Gsm.Network"
MODEM_SIMPLE="org.freedesktop.ModemManager.Modem.Simple"
MM="org.freedesktop.ModemManager"
GET_INFO="org.freedesktop.ModemManager.Modem.GetInfo"
GSM_NETWORK_SCAN="org.freedesktop.ModemManager.Modem.Gsm.Network.Scan" 
GSM_NETWORK_REG_INFO="org.freedesktop.ModemManager.Modem.Gsm.Network.GetRegistrationInfo"
MODEM_ENABLE="org.freedesktop.ModemManager.Modem.Enable"
Get_Esn="org.freedesktop.ModemManager.Modem.Cdma.GetEsn"
Get_Serving_System="org.freedesktop.ModemManager.Modem.Cdma.GetServingSystem"
Get_Registration_State="org.freedesktop.ModemManager.Modem.Cdma.GetRegistrationState"
###############################################################

################################################################
MM_ENUM=$(dbus-send --print-reply --system --dest=$MM \
    $DBUS_PATH $MM.EnumerateDevices |grep org | cut -c19-)
#################################################################
#***************** MAIN_LOOP_START + SET COUNTER  0 *************
#################################################################
COUNT=0
for DEV in $MM_ENUM
do
    COUNT=`expr $COUNT + 1`
    DEV=$(echo $DEV |sed s:\"::g)
    MM_DEVICE_INFO=$(dbus-send --print-reply --system --dest=$MM $DEV $GET_INFO |grep string | cut -c14-)
    MM_DEVICE_INFO=$(echo $MM_DEVICE_INFO |sed s:\"::g)
    MM_DEVICE_TYPE=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Type" |tail -n1|cut -c25-)
    MM_DEVICE_DRIVER=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Driver" |tail -n1|cut -c25-)
    MM_DEVICE_DRIVER=$(echo $MM_DEVICE_DRIVER |sed s:\"::g)
    MM_DEVICE_MASTER=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"MasterDevice" |tail -n1|cut -c25-)
    MM_DEVICE_MASTER=$(echo $MM_DEVICE_MASTER |sed s:\"::g)
    MM_DATA_DEVICE=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Device" |tail -n1|cut -c25-)
    MM_DATA_DEVICE=$(echo $MM_DATA_DEVICE |sed s:\"::g)
    MM_DATA_DEVICE_PIN_STAT=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"UnlockRequired" |tail -n1|cut -c25-)
    MM_DATA_DEVICE_IP=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"IpMethod" |tail -n1|cut -c25-)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
#########################################################################
# Need to see if device Enabled from MM_DATA_DEVICE_ENABLED true or false
# if false enable the device : else network info not available : WARNING :If connect by Network-Manager this will drop the connection
#########################################################################
    echo
    echo " ----*-----* MM-TEST DEVICE_ENABLE_DISABLE *-----*----"
    echo
    if [ $MM_DATA_DEVICE_ENABLED = "true" ]
    then
    echo " DEVICE ENABLED : true"
    echo " ACTION :disconnect"
    MM_DEVICE_ENABLE=$(dbus-send --print-reply --system --dest=$MM $DEV $MODEM_ENABLE boolean:false)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
    fi
################################################
    if [ $MM_DATA_DEVICE_ENABLED = "false" ]
    then
    echo " DEVICE ENABLED : false"
    echo " ACTION :enable"
    true = "(True)"
    MM_DEVICE_ENABLE=$(dbus-send --print-reply --system --dest=$MM $DEV $MODEM_ENABLE boolean:true)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
    echo " DEVICE ENABLE :$MM_DATA_DEVICE_ENABLED"
    fi
    if [ $MM_DATA_DEVICE_ENABLED = "false" ]
    then
    echo " SETTING ENABLE_DEVICE : fail"
    fi
###################################################
    echo
    echo " ----*-----* MM-TEST DEVICE_INFO *-----*----"
    echo
    echo " DEVICE :$COUNT"
    echo " MASTER_DEVICE :$MM_DEVICE_MASTER"
    echo " ENUMERATED DEVICE TYPE :$MM_DEVICE_TYPE"
    echo " DEVICE INFO :$MM_DEVICE_INFO"
##################################################
    if [ $MM_DEVICE_TYPE -eq 1 ]    
    then
    MODEM_TYPE="GSM"
    echo " MODEM TYPE :$MODEM_TYPE"
    dial="*99#"
    echo " DIAL COMMAND :$dial"
    MM_GSM_NETWORK_INFO=$(dbus-send --print-reply --system --dest=$MM $DEV $GSM_NETWORK_REG_INFO |grep string | cut -c14-)
    MM_GSM_NETWORK_INFO=$(echo $MM_GSM_NETWORK_INFO |sed s:\"::g)
    data=0
    for INFO in $MM_GSM_NETWORK_INFO
        do
            if [ $data -eq 0 ]
                then
                MCC=$(echo $INFO | cut -c -3)
                MNC=$(echo $INFO | cut -c 4-)
                echo " NETWORK MCC :$MCC"
                echo " NETWORK MNC :$MNC"
            fi
##########################################
            if [ $data -eq 1 ]
                then
                echo " PROVIDER   :$INFO"
            fi
##########################################
            if [ $data -eq 2 ]
                then
                echo " REGISTERED :$INFO"
            fi
##########################################
        data=`expr $data + 1`
        done
        echo
    fi
##################################################
    if [ $MM_DEVICE_TYPE -eq 2 ]
        then
        MODEM_TYPE="CDMA"
######### UNTESTED ##############################################
        echo " MODEM TYPE :$MODEM_TYPE"
        dial="#777"
        echo " DIAL COMMAND :$dial"
        MM_DEVICE_ESN=$(dbus-send --print-reply --system --dest=$MM $DEV $Get_Esn)
        echo $MM_DEVICE_ESN
        MM_DEVICE_SERVING_SYSTEM=$(dbus-send --print-reply --system --dest=$MM $DEV $Get_Serving_System |grep uint | cut -c14-) # 
        for INFO in $MM_DEVICE_SERVING_SYSTEM
            do
            echo $INFO
        done

        echo
    fi
##################################################
    echo " ----*-----* MM-TEST MM-INFO *-----*-----"
    echo
    echo " DRIVER :$MM_DEVICE_DRIVER"
    echo " DEVICE :/dev/$MM_DATA_DEVICE"
    echo " PIN STATUS :$MM_DATA_DEVICE_PIN_STAT"
##################################################
    if [ $MM_DATA_DEVICE_IP -eq 0 ]
        then
        echo " ENUMERATED IP METHOD :Use PPP to get the address."
    fi
##################################################
    if [ $MM_DATA_DEVICE_IP -eq 1 ]
        then
        echo " ENUMERATED IP METHOD :Static configuration, the modem will provide IP information."
    fi
##################################################
    if [ $MM_DATA_DEVICE_IP -eq 2 ]
        then
        echo " ENUMERATED IP METHOD :Use DHCP."
    fi
############## END OF UNTESTED ######################### show true then set false
    echo " DEVICE ENABLED :$MM_DATA_DEVICE_ENABLED"
    echo " ACTION :disconnect"
    MM_DEVICE_ENABLE=$(dbus-send --print-reply --system --dest=$MM $DEV $MODEM_ENABLE boolean:false)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
    echo " DEVICE ENABLE :$MM_DATA_DEVICE_ENABLED"
###################################################
    echo
    echo
done
#***************** MAIN_LOOP_END ************************
```

---

### Post by rmmb on 2012-01-05
Hi all. I decided to try ubuntu and following the instructions downloaded 11.10, created a USB pen and booted my hp laptop from there. When I tried my ZTE K3765-Z vodafone broadband pen to connect to the internet, ubuntu recognized the device, installed drivers, asked for the ZTE PIN and the pen changed the led color to intermittent dark blue, which is the normal behavior. The problem is that the final step, which is closing the connection doesn't happen. Any suggestions or recommendations? Thanks

SOLVED
I had just to do some configuration using the networking window

---

### Post by alexfish on 2012-02-22
This is for Huawei Devices , Next generation
 
**If only want to install drivers Look Here Post **              #[**75**]("http://ubuntuforums.org/showpost.php?p=11865849&postcount=75")

it will also depend on your kernel version , this Ubuntu 10.10

Here the device has switched (using ealier versions of usb modeswitch ) outputs from the usb-devices command notice the Cls, Sub and prot / normal 3g  these would be ff, ff, ff

Switched from 1446 to 
```
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```normal user would not think of using the option module
when in this state try and use Sakis3g to configure the modem,
Below are the Results
```
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```the device now recognised in Network Manager

in Ubuntu 11.04 you may only see One part of the device with the Option Driver
Here again try setting up the device with Sakis3g. if NM will not connect

Can see if these drivers are on the system cdc_wdm and qmi_wwan  , they may also work also keep a watch here                                    [http://www.draisberghof.de/usb_modeswitch/bb/]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=706&postdays=0&postorder=asc&start=15")
Have checked in **Ubuntu 11.04 cdc_wdm does exist** , ensure your system is up to date...**Updating Post # 60 accordingly **
  
if have Drivers installed from Huawei links , then the device will configure as close as the device needs to be IE , if the device has 3 modes then you will see three modes ,
if it has two modes you will see two modes , But the device may not be recognised by modem-manager , hence Network manager will not see the device. here again you can
use Sakis3g to get connected

here are the results of Ubuntu 11.04 with thr Huawei drivers
```
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=huawei_ether
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=huawei_ether
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
``` here ar the results of nm-tool
```
- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            huawei_ether
  State:             unavailable
  Default:           no
  HW Address:        00:1E:10:1F:00:01

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```as you can see the 3g device is not seen, so if the ether interface is not configured you can't connect
if the device has WiFi then it may connect. As for getting 3g connection , suggest using Sakis3g for ease of use , or ppp
have posted plenty on this thread , on different methods of getting connect.

Also note you can install the Huawei driver to allow third party access to the device + Switch logging Off , if Logging Stuck in Loop ,read the info and files ,supplied.
The modinfo
```
~$ modinfo hw_cdc_driver
filename:       /lib/modules/2.6.38-13-generic/kernel/drivers/net/usb/hw_cdc_driver.ko
license:        GPL
version:        v2.07.00.00
description:    Huawei ether driver for 3G data card ether device
author:         Franko Fang <huananhu@huawei.com>
srcversion:     866E62C8BF6445AE87CF101
alias:          usb:v12D1p*d*dc*dsc*dp*ic02isc0Dip00*
alias:          usb:v12D1p*d*dc*dsc*dp*ic02isc0DipFF*
alias:          usb:v12D1p*d*dc*dsc*dp*icFFisc02ip46*
alias:          usb:v12D1p*d*dc*dsc*dp*icFFisc02ip16*
alias:          usb:v12D1p*d*dc*dsc*dp*icFFisc02ip37*
alias:          usb:v12D1p*d*dc*dsc*dp*icFFisc02ip07*
alias:          usb:v12D1p*d*dc*dsc*dp*icFFisc01ip39*
alias:          usb:v12D1p*d*dc*dsc*dp*icFFisc01ip09*
alias:          usb:v12D1p*d*dc*dsc*dp*ic02isc06ipFF*
alias:          usb:v12D1p*d*dc*dsc*dp*ic02isc06ip00*
depends:        
vermagic:       2.6.38-13-generic SMP mod_unload modversions 686 
parm:           msg_level:Override default message level (int)
parm:           ncm_prefer_32:bool
parm:           ncm_prefer_crc:bool
parm:           ncm_tx_timeout:ulong
parm:           ncm_read_buf_count:uint
parm:           ncm_read_size_in1k:short
parm:           rt_debug:bool
```from the 
```
ls -al /dev/serial/by-id
``````
lrwxrwxrwx 1 root root  23 2012-02-22 22:35 usb-Huawei_Technologies_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB_utps_modem < as it say's the modem do not connect both 3g and DHCP
lrwxrwxrwx 1 root root  22 2012-02-22 22:35 usb-Huawei_Technologies_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB_utps_diag  < this is the control port for the  commands IE  for setting device and getting other data while connected ??
lrwxrwxrwx 1 root root  22 2012-02-22 22:35 usb-Huawei_Technologies_HUAWEI_Mobile-if04-port0 -> ../../ttyUSB_utps_pcui[ < this port continually returns the data from the device + commands sent to the ttyUSB_utps_diag 
```May find /dev/ttyUSB0 block by permissions / sakis3g can get around this
**[SIZE=2]if have used the eject script[/SIZE]** in the previous post with the ** arg tty** then the udev shows ttyUSB0 =  ttyUSB_utps_modem / and proves the above, so if the device is showing the ether interface without the Huawei Drivers Then Possibly Try the /devttyUSB0 or what ever shows to be the modem port,
One sure way to Connect to the Correct Port all the time , Go back to POST #2. If have Huawie Drivers then No Need to do this , all the info is in the rules, it note if the usb_modeswiitch rules Exist , Check the logging During Install, Its There To Help.
looks like the command to connect on ether interface is
> AT^NDISDUP=1,1,<my apn>  and the port is ttyUSB_utps_modemto disconect
```
AT^NDISDUP=1,0
```> Leave the Network Manager Ether interface setting to Manual
Once connected Then Click on NM Ether* interface and device should Connect or track the above link where it say's
**Can see if these drivers are on the system cdc_wdm and qmi_wwa**As Already Mentioned There are Plenty of ways To send commands to the ports .

**Also Note** , >  The eject script , This Can Be adapted for these Devices Please Read the Script
It will help with these sort of devices if Adapted Correctly, from seeing what it is , to getting Connected, and More
 **Its All there**.[B]But Leave The Original As is : IE Make A COPY

Say where line  [/B][FONT=monospace]"[/FONT]proc tty_status {tty} {[B] 
Add arg  : [/B]proc tty_status {tty AT} {
**AND LINE** : puts $serial "AT"
USE **puts $serial $AT**

**the parse lines EG**
```
if {$buff == "send"} {
set tty [lindex $argv 1]
set AT [[lindex $argv 2]
         tty_status $tty $AT

and the command
./eject send <tty> <your AT command>

```  Tip ADD another ARG tty2  to read the data and add a second serial port in the same Proc
Also remember the same port is used to connect 3g in the traditional manner should 4g not be available or the device can't work through the Ether Interface.

Please Do read all From Post #59 , even if Your device not From Huawei , more so ,if the ether interface
shows from the usb-devices command 

If get the Timings correct on the streaming port , you can then sort the data 
a lot of the command are ^ orientated but some at standard

EG:
^CPIN
^SYSINFO
AT+CSQ
^OPL
AT^PNN , 

Have Fun ,, tell you what this this is fun // if have mobile partner can look in the "log/mobilePartnerAT.txt"

if only using the driver then Ensure Correct data,  can get most of this from seviceproviders data-base on the system , standard AT commands are used for this Re First Post.

Just a note, if using Latest Version of Bam , if Have Unity  then do not minimise the BAM , use in another workspace , reason , it needs to be in the notification area
also read doc online help from the menus RE STK Functions <some of which are> provided by NSP 

For Now link to drivers: for the HMP try googling best source / re your provider may have released both 
[http://www.huaweidevice.com/tcpsdownload/downLoadCenter?category=&flay=software&downloadID=NDAzMjM=](http://www.huaweidevice.com/tcpsdownload/downLoadCenter?category=&flay=software&downloadID=NDAzMjM=)

Relevance:" If I can get the dongle to be recognised, would it then be possible to  run the included software (on the dongle) using either wine or Windows  XP in parallel to connect to the internet?"  POST  #[**1**]("http://ubuntuforums.org/showpost.php?p=11847881&postcount=1")

For mobile partner latest version try googling Mobile Partner 21 , make sure its, Linux version , re when on the site , it will indicate Linux , if not indicating Linux then avoid , have tested some of these sites , BAH , See Screen Shots , 3 is the drivers 4 is the inside of the Linux Mobile Partner  tar file
to install just use unzip at the location , the use terminal >  cd to where the files reside then ./install . 
follow prompts .

problem find official huawei driver/Mobile Partner : can try looking here : Use at Own Risk , Did an install of this , no Problems as of yet
[http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html](http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html)

**Sakis3g:** **THINK THIS IS A MUST DO IF CONNECTION IS APN** , sometimes HMP shows connected but no response from the lte-server
[http://www.sakis3g.org/](http://www.sakis3g.org/)

Tip if you want to monitor the stream use FOFF and connect to the LOG FILE

If everything is configured correctly then this is what you will see  with ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:14:2a:86:a5:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1e:10:1f:00:01  < This is the device
          inet addr:10.68.47.85  Bcast:10.68.47.87  Mask:255.255.255.252
          inet6 addr: fe80::21e:10ff:fe1f:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:209162 (209.1 KB)  TX bytes:62750 (62.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```Network Manager , not connected and connected RE nm-tool
```
- 
 Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            huawei_ether
  State:             disconnected
  Default:           no
  HW Address:        00:1E:10:1F:00:01

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:14:2A:86:A5:2C

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto eth1] ----------------------------------------------------
  Type:              Wired
  Driver:            huawei_ether
  State:             connected
  Default:           yes
  HW Address:        00:1E:10:1F:00:01

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.68.47.85
    Prefix:          30 (255.255.255.252)
    Gateway:         10.68.47.86

    DNS:             172.30.139.17
```Here is a screen shot using Huawei Mobile Partner,  Re SMS text message
second screen shot , shows request to purchase SMS text , so simple , just click on the url and browser fires up auto  connects to where you need to be . it Don't get  easier than that.
[B]
For Developers the easiest route to "c" programming the serial ports for these devices is to use cssl and use the call back function[/B]

using cssl

can be downloaded from

[http://sourceforge.net/projects/cssl/](http://sourceforge.net/projects/cssl/)

to make a lib.so

```
gcc -o libcssl.so cssl.c -shared -D_GNU_SOURCE -fPIC
```for other Read the Readme

to find what is in the lib try these commands

```
nm -D libcssl.so

nm --dynamic libcssl.so
```if looking to embed usb_modeswitch can apply same method  , download the source files then
```

gcc -o libmodeswitch.so usb_modeswitch.c -shared -D_GNU_SOURCE -fPIC
```using this route can save having to use wader

---

### Post by JimA52 on 2012-02-28
I've been through all of this stuff. Spent three days trying to get my Huawei E173 working. Support from Huawei is non-existent - I couldn't register on their site because they wouldn't accept my - valid - email address.

Anyway, after trying almost everything I tried installing Zorin - and amazingly it works. Even with an off the shelf Orange dongle, locked, and with the installation files visible. Just tested an O2 Dongle E1752 unlocked with the Orange SIM in and that works too. It must be that Zorin has all the drivers for the latest hardware. But no-one else seems to.

---

### Post by alexfish on 2012-03-01
> **JimA52 said:**
> I've been through all of this stuff. Spent three days trying to get my Huawei E173 working. Support from Huawei is non-existent - I couldn't register on their site because they wouldn't accept my - valid - email address.

Anyway, after trying almost everything I tried installing Zorin - and amazingly it works. Even with an off the shelf Orange dongle, locked, and with the installation files visible. Just tested an O2 Dongle E1752 unlocked with the Orange SIM in and that works too. It must be that Zorin has all the drivers for the latest hardware. But no-one else seems to.

You so Right

But There Again  >[http://zorin-os.com/tour.html](http://zorin-os.com/tour.html) > [http://developer.ubuntu.com/](http://developer.ubuntu.com/)

---

### Post by alexfish on 2012-03-08
> **JimA52 said:**
> I've been through all of this stuff. Spent three days trying to get my Huawei E173 working. Support from Huawei is non-existent - I couldn't register on their site because they wouldn't accept my - valid - email address.

Anyway, after trying almost everything I tried installing Zorin - and amazingly it works. Even with an off the shelf Orange dongle, locked, and with the installation files visible. Just tested an O2 Dongle E1752 unlocked with the Orange SIM in and that works too. It must be that Zorin has all the drivers for the latest hardware. But no-one else seems to.

Had to Take the Tour

Zorin is based on **Ubuntu** :P

If** Your From a windows background and New to Linux** . This could be the Place to Start

Zorin + Huawie Mobile Partner (thats if have a Huawie device) , got to be good.

So What do we have , Me thinks "**Windows Ubuntu (2012)**":P ... [http://zorin-os.com/index.html](http://zorin-os.com/index.html)

Have fun

Alexfish

---

### Post by neogy on 2012-03-14
I have been using olive wme102 modem using qualcomm driver the device id is 22f4:0021 which is is being detected by 

lsusb
showing
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b1e5 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
**Bus 002 Device 009: ID 22f4:0021  **


following your posts #59 and #60
i tried to configure the new data card provided by TATA Photon + with device id 2244:0021

root@neogy-K52F:~# lsusb -t -d 22f4:0021
1-1.5:1.2: No such file or directory
1-1.5:1.3: No such file or directory
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
        |__ Port 1: Dev 11, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 3: Dev 9, If 0, Class=stor., Driver=usb-storage, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 2: Dev 3, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
        |__ Port 2: Dev 3, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
        |__ Port 5: Dev 4, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 5: Dev 4, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
     [B]   |__ Port 5: Dev 4, If 2, Class=vend., Driver=, 12M
        |__ Port 5: Dev 4, If 3, Class=app., Driver=, 12M[/B]

root@neogy-K52F:~# ls -al /dev/serial/by-id/*
[B]ls: cannot access /dev/serial/by-id/*: No such file or directory
[/B]root@neogy-K52F:~# tar tf /usr/share/usb_modeswitch/configPack.tar.gz
03f0:002a
0421:060c
0421:0610
0421:0622
0421:0627
0471:1210:uMa=Philips
0471:1210:uMa=Wisue
0471:1237
0482:024d
04e8:689a
04e8:f000
057c:84ff
05c6:1000:sVe=GT
05c6:1000:sVe=Option
05c6:1000:uMa=AnyDATA
05c6:1000:uMa=Option
05c6:1000:uMa=SAMSUNG
05c6:1000:uMa=SSE
05c6:1000:uMa=Vertex
05c6:2000
05c6:2001
05c6:f000
05c7:1000
072f:100d
07d1:a800
07d1:a804
0930:0d46
0ace:2011
0ace:20ff
0af0:6711
0af0:6731
0af0:6751
0af0:6771
0af0:6791
0af0:6811
0af0:6911
0af0:6951
0af0:6971
0af0:7011
0af0:7031
0af0:7051
0af0:7071
0af0:7111
0af0:7211
0af0:7251
0af0:7271
0af0:7301
0af0:7311
0af0:7361
0af0:7381
0af0:7401
0af0:7501
0af0:7601
0af0:7701
0af0:7801
0af0:7901
0af0:7a01
0af0:7a05
0af0:8200
0af0:8201
0af0:8300
0af0:8302
0af0:8304
0af0:8400
0af0:8600
0af0:8800
0af0:8900
0af0:9000
0af0:c031
0af0:c100
0af0:d013
0af0:d031
0af0:d033
0af0:d035
0af0:d055
0af0:d057
0af0:d058
0af0:d155
0af0:d157
0af0:d255
0af0:d257
0af0:d357
0b3c:c700
0b3c:f000
0cf3:20ff
0d46:45a1
0d46:45a5
0df7:0800
0e8d:7109
0fce:d0cf
0fce:d0e1
0fce:d103
0fd1:1000
1004:1000
1004:607f
1004:613a
1004:613f
1004:6190
1033:0035
106c:3b03
106c:3b05
106c:3b06
1076:7f40
1199:0fff
1266:1000
12d1:1001
12d1:1003
12d1:1009
12d1:101e
12d1:1030
12d1:1031
12d1:1414
12d1:1446
12d1:1449
12d1:14ad
12d1:14b5
12d1:14b7
12d1:14c1
12d1:14c4
12d1:14c5
12d1:14d1
12d1:14fe
12d1:1505
12d1:1520
12d1:1521
12d1:1523
12d1:1553
12d1:1557
12d1:1c0b
12d1:1da1
12d1:380b
1307:1169
1410:5010
1410:5020
1410:5030
1410:5031
1410:5041
148e:a000
148f:2578
16d8:6281
16d8:6803
16d8:700a
16d8:700b
16d8:f000
198a:0003
198f:bccd
19d2:0003
19d2:0013
19d2:0026
19d2:0040
19d2:0053
19d2:0083
19d2:0101
19d2:0103
19d2:0110
19d2:0115
19d2:0149
19d2:1001
19d2:1007
19d2:1009
19d2:1013
19d2:1171
19d2:1175
19d2:1179
19d2:1201
19d2:1216
19d2:1224
19d2:2000
19d2:bccd
19d2:ffe6
19d2:fff5
19d2:fff6
1a8d:1000
1ab7:5700
1b7d:0700
1bbb:f000
1c9e:1001
1c9e:6061
1c9e:9200
1c9e:9800
1c9e:9e00
1c9e:f000
1dd6:1000
1e0e:f000
1edf:6003
1ee8:0009
1ee8:0013
1ee8:0040
1f28:0021
1fac:0032
1fac:0130
201e:2009
2020:f00e
230d:0001
230d:0007
8888:6500
**The device is not listed in the list**

root@neogy-K52F:~# cd /etc/usb_modeswitch.d
root@neogy-K52F:/etc/usb_modeswitch.d# tar -x 22f4:0021 -f /usr/share/usb_modeswitch/configPack.tar.gz
[B]tar: 22f4\:0021: Not found in archive
tar: Exiting with failure status due to previous errors[/B]
root@neogy-K52F:/etc/usb_modeswitch.d# usb_modeswitch -W -c /etc/usb_modeswitch.d/22f4:0021

Reading config file: /etc/usb_modeswitch.d/22f4:0021

 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.1.9 (C) Josua Dietze 2011
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x224f
DefaultProduct= 0x0021
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    0xff
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent="5553424312345678000000000000061e000000000000000000000000000000"
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000"
NeedResponse=1
ResponseEndpoint= not set
Interface=0x00

InquireDevice enabled (default)
Success check enabled, max. wait time 10 seconds
System integration mode disabled

usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 011 on 002
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 009 on 002
usb_os_find_devices: Found 002 on 002
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 004 on 001
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 003 on 001
skipping descriptor 0xB
skipped 1 class/vendor specific endpoint descriptors
skipped 6 class/vendor specific interface descriptors
skipping descriptor 0x25
skipped 1 class/vendor specific endpoint descriptors
skipped 9 class/vendor specific interface descriptors
usb_os_find_devices: Found 002 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
error obtaining child information: Inappropriate ioctl for device

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
  searching devices, found USB ID 046d:c016
  searching devices, found USB ID 22f4:0021
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 0b05:1788
  searching devices, found USB ID 04f2:b1e5
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
 No devices in default mode found. Nothing to do. Bye.

root@neogy-K52F:/etc/usb_modeswitch.d# grep -i v22f4p0021 /lib/modules/`uname -r`/modules.alias
root@neogy-K52F:/etc/usb_modeswitch.d# grep -i v22f4p0021 /lib/modules/*/modules.alias
root@neogy-K52F:/etc/usb_modeswitch.d# 

[B]returns nothing means not found in kernel
(following post #60)

[/B]root@neogy-K52F:/etc/usb_modeswitch.d# grep usb /sys/bus/usb/devices/*/modalias
/sys/bus/usb/devices/1-0:1.0/modalias:usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/1-1:1.0/modalias:usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00
/sys/bus/usb/devices/1-1.2:1.0/modalias:usb:v04F2pB1E5d2069dcEFdsc02dp01ic0Eisc01ip00
/sys/bus/usb/devices/1-1.2:1.1/modalias:usb:v04F2pB1E5d2069dcEFdsc02dp01ic0Eisc02ip00
/sys/bus/usb/devices/1-1.5:1.0/modalias:usb:v0B05p1788d0449dcE0dsc01dp01icE0isc01ip01
/sys/bus/usb/devices/1-1.5:1.1/modalias:usb:v0B05p1788d0449dcE0dsc01dp01icE0isc01ip01
/sys/bus/usb/devices/1-1.5:1.2/modalias:usb:v0B05p1788d0449dcE0dsc01dp01icFFiscFFipFF
/sys/bus/usb/devices/1-1.5:1.3/modalias:usb:v0B05p1788d0449dcE0dsc01dp01icFEisc01ip01
/sys/bus/usb/devices/2-0:1.0/modalias:usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00
/sys/bus/usb/devices/2-1:1.0/modalias:usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00
/sys/bus/usb/devices/2-1.1:1.0/modalias:usb:v046DpC016d0340dc00dsc00dp00ic03isc01ip02
/sys/bus/usb/devices/2-1.3:1.0**/modalias:usb:v22F4p0021d0000dc00dsc00dp00ic08isc06ip50**

using ip50

grep -i ip50 /lib/modules/`uname -r`/modules.alias
alias usb:v*p*d*dc*dsc*dp*ic08isc06ip50* uas
alias usb:v*p*d*dc*dsc*dp*ic08isc06ip50* usb_storage
alias usb:v*p*d*dc*dsc*dp*ic08isc05ip50* usb_storage
alias usb:v*p*d*dc*dsc*dp*ic08isc04ip50* usb_storage
alias usb:v*p*d*dc*dsc*dp*ic08isc03ip50* usb_storage
alias usb:v*p*d*dc*dsc*dp*ic08isc02ip50* usb_storage
alias usb:v*p*d*dc*dsc*dp*ic08isc01ip50* usb_storage
root@neogy-K52F:/etc/usb_modeswitch.d# 


[B]which means the device is not getting detected as modem Please put some light!!!
[/B]root@neogy-K52F:/etc/usb_modeswitch.d# usb-devices 

T:  Bus=02 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=22f4 ProdID=0021 Rev=00.00
S:  Manufacturer=Qualcomm, Incorporated
S:  Product=USB MMC Storage
S:  SerialNumber=00100_DATACAR
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
root@neogy-K52F:/etc/usb_modeswitch.d# 
**Please put some light!!!**

---

### Post by alexfish on 2012-03-15
Hi @ neogy

can see from private message , have configured Huawei device using info in the HOW TO:

OK:

Each device is different:

First step is to see what mode the device is in : all info indicates = unswitched

Un_switched devices Need to be switched to Modem Mode , this can be done in Two ways , eject(cd part of the device) or send message to the device (message mode switching) , this is what usb_modeswitch does , usb_modeswitch can do both

usb_modeswitch needs to know what the device is , hence the data base

From the end user aspect you have to "decide" which method will switch the device

For this first step I have written a script which may help , see post               #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61")

it does most of what has been done manually by yourself.

read the post carefully , the script will give the info necessary for the decision making process:

1. will the device switch with the eject command "finding the eject bit" , or does it require "mode switch message"
   Also note from "first post" foot of page screen shot , finding an eject-able device,

2. Device not switching with eject Command and not in data base , refer to mode_switch forum
    even if the device switches with the eject command please inform the forum of the finding.

3. the script will detect if the drivers are loading after switching , if not loading then will run through the next stage

See what happens, for help on the script can send private message.
Also noted
**Bus 002 Device 009: ID 22f4:0021  **





> 
following your posts #59 and #60
i tried to configure the new data card provided by TATA Photon + with device id 2244:0021

root@neogy-K52F:~# lsusb -t -d 22f4:0021
1-1.5:1.2: No such file or directory
1-1.5:1.3: No such file or directory
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
        |__ Port 1: Dev 11, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 3: Dev 9, If 0, Class=stor., Driver=usb-storage, 12M <<< This is your Device
Ref ::lsub = **Bus 002 Device 009: ID 22f4:0021  **
Also worth looking up
[http://comments.gmane.org/gmane.linux.usb.general/34876](http://comments.gmane.org/gmane.linux.usb.general/34876)
Have Done link to PDF doc RE: 12M at post #60

alexfish

---

### Post by fentan4562 on 2012-04-17
I must be stupid as i dont get how to install my e353 dongle on 11.04 at all could do with SIMPLE instructions i tried for 6hrs and all i got was drunk with frustration not being a computer programer i had no chance guidance would be very helpfull.
:D

---

### Post by coffeecat on 2012-04-17
> **fentan4562 said:**
> I must be stupid as i dont get how to install my e353 dongle on 11.04 at all could do with SIMPLE instructions

The simplest instruction I can suggest is to upgrade to, or do a fresh install of Ubuntu 11.10. Or wait a couple of weeks and install 12.04. The Huawei E353 "just works" in both 11.10 and 12.04. All you do is to plug the dongle in, wait a couple of minutes and then click on the network manager icon near the top right. You'll see a mobile broadband choice in the drop-down menu. Click on this, follow the wizard and you'll soon be connected.

You do have to wait a couple of minutes - at least - for the device to be detected and for the network manager drop-down menu to show you the mobile broadband choice.

---

### Post by alexfish on 2012-04-18
> **coffeecat said:**
> The simplest instruction I can suggest is to upgrade to, or do a fresh install of Ubuntu 11.10. Or wait a couple of weeks and install 12.04. The Huawei E353 "just works" in both 11.10 and 12.04. All you do is to plug the dongle in, wait a couple of minutes and then click on the network manager icon near the top right. You'll see a mobile broadband choice in the drop-down menu. Click on this, follow the wizard and you'll soon be connected.

You do have to wait a couple of minutes - at least - for the device to be detected and for the network manager drop-down menu to show you the mobile broadband choice.

Thanks for the input,

Can post details of this device , using the command "usb-devices"

Then can see if the Device has Configured in the manor to which it operates. and the drivers associated.

Can do both for 11.10 and possible 12.04 only then will be convinced of certain aspects of this device and others in this family of Huawei Next generation

have tested this device on versions of Ubuntu as listed in the How To , depending on kernel and  version  of usb_modeswitch it can have different configurations. 

Thanks in advance

alexfish

---

### Post by coffeecat on 2012-04-18
> **alexfish said:**
> Can post details of this device , using the command "usb-devices"

@alexfish, sorry to interfere in your thread, but I just happened across fentan4562's post yesterday minutes after posting in another thread about this Huawei device. :) Anyway, the relevant output of usb-devices in Oneiric/11.10:

```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

I'll boot up 12.04 later and edit this post with the output from Precise.

**EDIT**: Equivalent part of output from 12.04 on different machine:

```
T:  Bus=02 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

---

### Post by alexfish on 2012-04-19
> **fentan4562 said:**
> I must be stupid as i dont get how to install my e353 dongle on 11.04 at all could do with SIMPLE instructions i tried for 6hrs and all i got was drunk with frustration not being a computer programer i had no chance guidance would be very helpfull.
:D

Yip

Can understand , these new devices ? each device is different , there is no simple one instruction , if it does not work

See the post above . For a Novice that would be a step in the right direction , Latest Versions of Ubuntu.

I can Tell this device is going to connect , If had read carefully though post relating to Huawei next generation , it is highlighted in First Post

Also Highlight in the First Post and Still have Problems , Start New Thread in Network an Wireless

posting relevant info about the device , using Commands from the terminal

IE:
```
usb-devices
```or
```
 lsusb -t
```then start new thread here
 [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")

Posting the relevant info in your New Thread , can also say if Laptop or Desktop , myself or someone else with experience of the device may respond to Your Thread , also highlight the model 
HUAWEI 353 , in the Title

Regards

alexfish

---

### Post by alexfish on 2012-04-22
> **coffeecat said:**
> @alexfish, sorry to interfere in your thread, but I just happened across fentan4562's post yesterday minutes after posting in another thread about this Huawei device. :) Anyway, the relevant output of usb-devices in Oneiric/11.10:

```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```I'll boot up 12.04 later and edit this post with the output from Precise.

**EDIT**: Equivalent part of output from 12.04 on different machine:

```
T:  Bus=02 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```

As seen this device will connect , yet the ether driver has not loaded ,** to get full functionality of the device** then

**Suggestion :How to install Huawie Driver Modules**

make folder in Downloads "huawei-drivers"

download the drivers from here:
[http://www.huaweidevice.com/tcpsdown...oadID=NDAzMjM=]("http://www.huaweidevice.com/tcpsdownload/downLoadCenter?category=&flay=software&downloadID=NDAzMjM=")

copy the tar file to the folder huawei-drivers , > rightclick on the tarfile > select from menu "Extract Here"

open up a terminal
```
sudo su
``````
cd `pwd`/Downloads/huawei-drivers/driver/ndis_driver/ndis_src
``````
./make_driver.sh
```close the terminal

open terminal
```
cd `pwd`/Downloads/huawei-drivers/driver
``````

sudo cp ./usbmod /usr/bin/usbmod
```To ensure drivers are loading
```
lsusb
```example reply:
```
Bus 002 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:1506 Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 059b:047a Iomega Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```example to load option driver + huawei_ether
```
sudo usbmod load 1506
```[B]For other functions of the usbmod read the script "usbmod"

[/B]Example of configured device:
```
usb-devices
```reply
```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=huawei_ether
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=huawei_ether
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

```

---

### Post by coffeecat on 2012-04-23
> **alexfish said:**
> As seen this device will connect , yet the ether driver has not loaded ,

Yes, that is curious, but I was getting ~200 Kb/s download speed in a fairly weak signal area. Which is why I didn't investigate further.

---

### Post by alexfish on 2012-04-23
> **coffeecat said:**
> Yes, that is curious, but I was getting ~200 Kb/s download speed in a fairly weak signal area. Which is why I didn't investigate further.
Don't think connecting standard 3g I.E.. When connecting by apn makes any deference in the download speed 

the difference of using the ETH* interface with NM is this

1. it frees up the modem port for 3rd party access such as Gammu or Wammu for sms
2. retrieval of other info , you mentioned one , Signal Strength
3. makes for easy bridging or sharing the connection

ADDED: have adapted the script "usbmod" to auto-load the drivers
 can edit the script to :-
```
#! /bin/bash
##############################################################
# ADDED auto detect
# command = sudo usbmod auto
##############################################################
if [ "$1" == "remove" ]
then
    if [ "$(/sbin/lsmod |grep pl2303)" != "" ]
    then 
        /sbin/rmmod -f pl2303
    fi
elif [ "$1" == "update" ]
then
    if [ "$(/sbin/lsmod |grep option)" != "" ]
    then
        /sbin/rmmod -f option
    fi
    if [ "$(/sbin/lsmod |grep pl2303)" != "" ]
    then 
        /sbin/rmmod -f pl2303
    fi
    
    if [ "$(/sbin/lsmod |grep usbserial)" != "" ]
    then
        /sbin/rmmod -f usbserial
    fi

    /sbin/modprobe usbserial vendor=0x12d1 product=$2    

elif [ "$1" == "load" ]
then
    /sbin/modprobe hw_cdc_driver
    /sbin/modprobe option
    echo 12D1 $2 > /sys/bus/usb-serial/drivers/option1/new_id
    /bin/touch /dev/huawei_mobile
###################################################
elif [ "$1" == "auto" ]
then
    product_id=$(lsusb | grep 12d1)
    product_id=$(echo $product_id | cut -c 29-)
    product_id=$(echo $product_id | cut -c -4)
    /sbin/modprobe hw_cdc_driver
    /sbin/modprobe option
    echo 12D1 $product_id > /sys/bus/usb-serial/drivers/option1/new_id
    /bin/touch /dev/huawei_mobile
##################################################
elif [ "$1" == "unload" ]
then

        #Update for DTS2011050500830 lxz 20110520 
    #/sbin/rmmod -f option
    /sbin/rmmod option
    /sbin/modprobe option
    /bin/rm -f /dev/huawei_mobile
elif [ "$1" == "bindusbstorage" ]
then

    for SEG in f7 f8 f9 f10 f11 f12 f13 
    do
        PORT=$(echo $2 | cut -d / -$SEG)
        if [ "$(echo $PORT |grep : )" != "" ] 
        then
            break
        fi
        done
    echo -n $PORT > /sys/bus/usb/drivers/option/unbind

    if [ "$(/sbin/lsmod |grep usb_storage)" != "" ]
    then 
        echo -n $PORT > /sys/bus/usb/drivers/usb-storage/bind
    else
        /sbin/modprobe usb-storage
                echo -n $PORT > /sys/bus/usb/drivers/usb-storage/bind
    fi

else

    SYS_KERN_VER=`uname -r`
    if [ "$SYS_KERN_VER" \< "2.6.25" ]
    then
        echo "Huawei NDIS can not support Current system"
    else
        for SEG in f7 f8 f9 f10 f11 f12 f13 
        do
            PORT=$(echo $1 | cut -d / -$SEG)
            if [ "$(echo $PORT |grep : )" != "" ] 
            then
                break
            fi
                done
        echo -n $PORT > /sys/bus/usb/drivers/option/unbind

        if [ "$(/sbin/lsmod |grep hw_cdc_driver)" != "" ]
        then 
            echo -n $PORT > /sys/bus/usb/drivers/huawei_ether/bind
        else
            /sbin/modprobe hw_cdc_driver
        fi
    fi
    
    if [ "$(/sbin/lsmod |grep usb_storage)" == "" ]
    then
        /sbin/modprobe usb-storage
    fi
    
fi
```
**Note: Read through the script : It can easy adapt for any driver Module, it may get you out of trouble**  : RE POST  #[**60**]("http://ubuntuforums.org/showpost.php?p=11444511&postcount=60")
look at line " echo 12D1 $product_id" , the 12D1 could be change to say for zte "19D2" etc , etc

---

### Post by alexfish on 2012-04-26
**HOW TO GET THE INFO FROM HUAWEI** next generation devices

Here assuming have installed Huawei drivers only and not the rules: POST   			#[**75**]("http://ubuntuforums.org/showpost.php?p=11865849&postcount=75")

read this and the info carefully before committing : Here this device uses /dev/ttyUSB2 for configuration data and my APN = [COLOR=Blue]3internet[/COLOR]

you will have to check which port your devices use , there are plenty of how to find the ports in this thread

also can use the script posted::POST #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61")

open up first terminal
```
cat /dev/ttyUSB2
```open up second terminal
```
echo -e "ATZ\r" > /dev/ttyUSB2
``````
echo -e "AT^NDISDUP=1,1,[COLOR=Blue]3internet[/COLOR]\r" > /dev/ttyUSB2
``````
echo -e "AT^DHCP?\r" > /dev/ttyUSB2
```gives out
```
DHCP:[COLOR=Blue]cd953a0a,fcffffff,ce953a0a,ce953a0a,118b1fac[/COLOR],118b1eac,21600000,0
```decode the message
```
perl -e 'print join(",",map { join(".", unpack("C4", pack("L", hex))) } split /,/, shift),"\n"' cd953a0a,fcffffff,ce953a0a,ce953a0a,118b1fac

```gives something like
```
10.58.149.205,255.255.255.252,10.58.149.206,10.58.149.206,172.31.139.17
```results = now can configure the interface
> eth* 10.58.149.205 netmask 255.255.255.252
default route 10.58.149.206
server 172.31.139.17

Have Fun

alexfish

---

### Post by alexfish on 2012-04-27
**This will be MY final post in this HOW TO **, **as you Know things are changing : **                                                                [Pending Changes to Tutorials and Tips.]("http://ubuntuforums.org/showthread.php?t=1949027") 

**Follow on From Post:**             #[**78**]("http://ubuntuforums.org/showpost.php?p=11875851&postcount=78")

in the absence of tcl.
For nearest serial driver for qmi (hex protocol) 
suggest installing "**libdevice-serialport-per**l" it mimics mscom , now you know the roots!!!!

there is a exec file modemtest

use the man pages "man modemtest"

then test IE:
```
modemtest --hide-possible /dev/ttyUSB0
```typical reply
```
Device::SerialPort v1.40.0 loaded.
Port '/dev/ttyUSB0' open
can ioctl: Yes
Got handshake: none
Got baud: 9600
Got databits: 8
Got parity: none
Got stopbits: 1
Modem status = 0x0166 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=ON )

Activated DTR(okay) and RTS(okay) ... pausing for 3 seconds
Modem status = 0x0166 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=ON )

Deactivated DTR(okay) and RTS(okay) ... pausing for 3 seconds
Modem status = 0x0160 (DTR=off CTS=ON  RTS=off DSR=ON  RNG=off CD=ON )

Activated DTR(okay) ... pausing for 3 seconds
Modem status = 0x0162 (DTR=ON  CTS=ON  RTS=off DSR=ON  RNG=off CD=ON )

Activated RTS(okay) ... pausing for 3 seconds
Modem status = 0x0166 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=ON )

read: 0
saw -><-
wrote: 5
written ->ATE1{0x0D}<-
read: 11
saw ->ATE1{0x0D}{0x0D}{0x0A}OK{0x0D}{0x0A}<-  NOTE THIS OUTPUT
read: 0
saw -><-

Modem status = 0x0166 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=ON )
Port closed
```Suggest sudo gedit /usr/bin/modemtest
then "save as" > "modemtest" in home directory 

This script can be adapted to get the info and also connect via ndis or qmi protocol , Please note this applies to both ttyUSB*(option) and ttyACM*(CDMA) ,also both can be configured to use usbserial, the script at POST              #[**77**]("http://ubuntuforums.org/showpost.php?p=11866235&postcount=77")  can sort this if no driver loading , but will also have to install the Huawie driver for the ether port

the same perl serial driver should also connect to other second generation devices such as ZTE

here is a pointer to some of what all this is about "google qmi perlscript linux"
and look here : [http://markmail.org/message/fzzuqmuokhtgjhxt](http://markmail.org/message/fzzuqmuokhtgjhxt)

also read this extract:
```
1) request a client ID for the QMI_WDS subsystem:      perl -e 'print pack("C*", map { hex } @ARGV)' 1 f 0 0 0 0 0 1 22 0 4 0 1 1 0 1 >/dev/cdc-wdm2      you will need to parse the ID from reply for the next command.  It     will be the very last byte in the reply (assumin success).  Initially    it will also most likely be 1.  2) send a start connction message:      perl -e 'print pack("C*", map { hex } @ARGV)' 1 c 0 0 1 3 0 2 0 20 0 0 0 >/dev/cdc-wdm2                                      "3" is the client ID ---^     the reply will contain a 4 byte handle which you will need to     disconnect.  That's it!
```

source : [http://lists.openwall.net/netdev/2012/01/20/7](http://lists.openwall.net/netdev/2012/01/20/7)
Have fun 

alexfish

PS: also check the examples in the "/usr/share/doc/libdevice-serialport-perl/examples/"

---

### Post by lisati on 2012-04-27
Closed by request of OP

---

