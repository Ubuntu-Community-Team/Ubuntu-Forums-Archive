---
title: "SBC Yahoo DSL!--What a pain to connect"
date: 2008-08-05
forum: The Cafe
---

### Post by sports fan Matt on 2008-08-05
I have been sitting on a non working computer although im not sure why since Yesterday.  All the lights and everything is connected through the router although I cannot connect to Firefox.  I ran across a help page which didnt help that much so my question is what may I need to change in my network to get it connected or what else can I try?

---

### Post by Icehuck on 2008-08-05
> **sox fan Matt said:**
> I have been sitting on a non working computer although im not sure why since Yesterday.  All the lights and everything is connected through the router although I cannot connect to Firefox.  I ran across a help page which didnt help that much so my question is what may I need to change in my network to get it connected or what else can I try?

I shouldn't even offer this bit of help since you're a south sider. ;)

Is your router storing the user ID and password for your sbc account? If it is you probably need to set your DSL modem to go into bridge mode. Unplug your router and direct wire to your modem. See if you can connect like that. If you can then you need to set your modem to bridge mode.

Go CUBS.

---

### Post by sports fan Matt on 2008-08-05
I havent even gotten that far as to obtain the sbc yahoo user id and password, but i'll try it when I can attempt to reach a human @ SBC.  I tried for an hour an a half and gave up yesterday.  

Off topic:  the weather last night was crazy, we had tornadoes roll through a few blocks from here. The cubs game was stop even with the players on the field with the lightning strike!

---

### Post by Icehuck on 2008-08-05
> **sox fan Matt said:**
> I havent even gotten that far as to obtain the sbc yahoo user id and password, but i'll try it when I can attempt to reach a human @ SBC.  I tried for an hour an a half and gave up yesterday.  

Off topic:  the weather last night was crazy, we had tornadoes roll through a few blocks from here. The cubs game was stop even with the players on the field with the lightning strike!

AH, ok then you don't have an active internet account with them yet. You can call them and get a user id and password setup and then you can store them into your router. Still have to switch the modem over to "bridge" mode though. Or if you have a windows machine you can use the software to register yourself an account.

---

### Post by Dragonbite on 2008-08-05
I had a lot of trouble and had to dance between using Windows and IE to get my account set up, and using Linux and firefox to access the modem (Windows could not).

Eventually I got it all situation, yet I'm not sure how.  I may have had to connect the windows machine via dial-up to access the site.

It was a long, painful night that my psyche has supressed since then.

---

### Post by Icehuck on 2008-08-05
> **Dragonbite said:**
> I had a lot of trouble and had to dance between using Windows and IE to get my account set up, and using Linux and firefox to access the modem (Windows could not).

Eventually I got it all situation, yet I'm not sure how.  I may have had to connect the windows machine via dial-up to access the site.

It was a long, painful night that my psyche has supressed since then.

Wow, when I had SBC Yahoo it wasn't even remotely difficult to setup. I had dsl up and running in less than 20 minutes.

---

### Post by frrobert on 2008-08-05
The initial setup of the account looks for Windows and IE.  You may need to borrow a Windows PC to setup the account or you could try IE4Linux if you have it installed.

Once the account and modem is setup SBC Yahoo works fine with Linux.

---

### Post by mips on 2008-08-05
> **Icehuck said:**
> Still have to switch the modem over to "bridge" mode though. Or if you have a windows machine you can use the software to register yourself an account.

](*,)](*,)](*,)

Why do people insist on doing this and making their lives difficult? If you put the router into bridged mode you have to configure a PPPoE client on the PC side and let the PC do the routing, why? This is extra work and complication.

Why not let the router do what it was supposed to do in the first place? Just configure the router with the userid/passwd and set the correct encapsulation type. Nothing more to it and any pc that connects to it will simply work via DHCP without requiring it's own PPPoE client.

---

### Post by Icehuck on 2008-08-05
> **mips said:**
> ](*,)](*,)](*,)

Why do people insist on doing this and making their lives difficult? If you put the router into bridged mode you have to configure a PPPoE client on the PC side and let the PC do the routing, why? This is extra work and complication.

Why not let the router do what it was supposed to do in the first place? Just configure the router with the userid/passwd and set the correct encapsulation type. Nothing more to it and any pc that connects to it will simply work via DHCP without requiring it's own PPPoE client.


SBC (in the Chicagoland area)either gives you a speedstream modem or a 2wire router. If you get the modem, you have to enable bridging mode(on the MODEM) to have your personal router manage the connection.

---

### Post by wolfen69 on 2008-08-05
if you have a router connected, disconnect it for now. go right from the modem to the computer. open a browser and type in 192.168.0.1  enter the account name and password. then enter the modem ID# located at the bottom of the unit. that's all i had to do to get mine going. you do not need windows for this.

---

### Post by CouchMaster on 2008-08-05
Step 3: Activating your AT&T Yahoo! High Speed Internet account and setting up your Internet connection
 
	

Now that your computer is connected to the DSL Modem, you need to activate your AT&T Yahoo! High Speed Internet account.
To activate your AT&T Yahoo! High Speed Internet account:

   1. Open your Internet browser.

   2. Type [http://192.168.0.01](http://192.168.0.01) into the browser&#8217;s address line.

   3. If prompted, enter the Access Code found on the bottom of the DSL Modem and click NEXT.

   4. You will be prompted to enter a username and password. To access the AT&T Yahoo! High Speed Internet registration servers, you must enter the following username and password:

      Username: [email]sbcyahooreg@sbcglobal.net[/email]
      Password: sbcyahooreg

   5. Click Save Changes.

   6. The connection process will begin. During the connection process, the lights on the front of the DSL Modem will first blink green then turn solid green. This step could take a couple of minutes.

   7. At this point of your installation you are connected to the AT&T Yahoo! High Speed Internet registration server and you are NOT connected to the Internet.
   8. To begin the AT&T Yahoo! High Speed Internet Member registration process, type the following URL into the Address field of your Internet browser:

      [https://sbcreg.sbcglobal.net](https://sbcreg.sbcglobal.net)

      Note: The address must be entered exactly including the &#8220;s&#8221; after the http or the program will not run.

   9. Follow the on screen instructions to complete the AT&T Yahoo! High Speed Internet registration process.

      Note: At the end of the AT&T Yahoo! High Speed Internet registration process, you may see a BLANK (all white) page. If so, simply continue with the steps below and ignore this page.

  10. To finish the installation process and connect your DSL Modem to the Internet, you must configure your DSL Modem with the Member ID and password you selected during AT&T Yahoo! High Speed Internet registration.

      To do so, repeat steps 1 though 6 above. In step 4, enter the Member ID and Password that you created during the registration process. Click Save Changes.


  11. The DSL Modem will now connect to the Internet. This process may take several minutes.

---

### Post by sports fan Matt on 2008-08-05
I'll try this and report back.  Will it fetch an error from ff even if my router is connected saying "page can not be displayed" or something like that?

---

### Post by sports fan Matt on 2008-08-05
this apparently refused to work.  Even after going down and explaining my issue I cant seem to get anywhere, the connection in my browser times out...:(

---

### Post by mips on 2008-08-05
Can you ping the routers IP address?
Does the router assign you a DHCP address or do you statically configure it?
Is your PC & router in the same network?
What output does route -n provide?
What output does ifconfig -a provide?

You need to give us more info. I'm off to bed now, hopefully your problem will be sorted in the meantime.

---

### Post by sports fan Matt on 2008-08-05
#3 Yes
#4 I'll let you know, im on a windows machine right now but will post back
#5 see #4
1.  Not sure by pinging I assume you said Type [http://192.168.0.01](http://192.168.0.01) into the browser’s address line. which results in a timed out connection error.  
2.  Not sure, anyway I can find out? 

Sorry for being such a NooB:lolflag:

---

### Post by sports fan Matt on 2008-08-05
I got my account number...things are looking up

---

### Post by Methuselah on 2008-08-06
I remember when I was runnign windows only and trying to connect with installing the crapware CD.
I just could not get it to work!

I think I ended up installing to get it going then removing.
I was annoyed then and would be more annoyed now when I'm using mostly linux.

---

### Post by sports fan Matt on 2008-08-06
I just keep thinking it shouldnt be this hard...:lolflag:

---

### Post by Methuselah on 2008-08-06
> **sox fan Matt said:**
> I just keep thinking it shouldnt be this hard...:lolflag:

It should be easy.
It's ridiculous that's what it is.
It really irks me sometimes how everyone is looking for an excuse to install donotwant-ware to give you functionality you DO want.
As bad as windows is, I'm sure it can connect to the internet without help from an SBC CD that changes my homepage to yahoo and installs toolbars.

---

### Post by mips on 2008-08-06
You are not supplying enough info.

1. Please post output of **ifconfig eth0  ** (Depends on your interface number)
2. Please post output of **ping 192.168.0.1**
 3. Please post output of **lspci | grep Eth**
 4. Please post output of **route -n**
 5. Please post output of **cat /etc/resolv.conf**
 6. Please post output of **cat /etc/network/interfaces**
 7. Please post output of **cat /etc/dhcp3/dhclient.conf**
 8. Please copy entire output of **[COLOR=Red]windows[/COLOR] ipconfig /all **command here if you have windows installed

---

### Post by sports fan Matt on 2008-08-06
Sorry I havent had a chance to post those commands as of yet, I will shortly, but just 1-7 as I dont have a windows machine

---

### Post by sports fan Matt on 2008-08-06
1.  link ethernet hw add 02e324mtu 1600 metric ex packets 0 tx packets 0 rx bytes 0 interrupt 9

2.  destination host unreachible
3.  I couldnt get #3
4.  destination 169.254.0.0 genmask 255.255.0
5.  name server (search eden local) thats my building but shouldnt flare up because I switched the wires monday to att, just not sure how to configure the network to sbc's network..
6.  auto lo loiface inet loopback iface eth inet dhcp

Sorry if I didnt copy the commands exactly but Since I cant get online i had to copy them then bring them to a windows pc..I hope I helped with what you asked for

---

### Post by mips on 2008-08-06
That does not really tell me what I want to know but looking at #4 tells me you have no IP Configuration. Keep in mind that you can always pipe your output to a text file and copy it to a usb flash key to display here.

My advice to you would be to statically configure your Ethernet interface with the following parameters (Assuming your router is in the 192.168.0.0 network):

IP Address: 192.168.0.11
Default Gateway: 192.168.0.1
Netmask: 255.255.255.0
Broadcast Address: 192.168.0.255
DNS: 208.67.222.222

You can do this in the **/etc/network/interfaces **file** (**DNS in** /etc/resolv.conf**) or you can do it via System->Administration->Network or something like that in Gnome.

After this you should be able to connect to the router from a web browser by entering 192.168.0.1 as the address.

---

### Post by sports fan Matt on 2008-08-06
Thanks for the help.  Yeah I havent been able to set up my account just yet, because I couldnt get to the regristration page, there no ip address..I Will try this config and report back :)

---

### Post by sports fan Matt on 2008-08-07
After another hour with tech support and them "telling me, your operating system may not be supported" I am about to im not sure.  Is this such a problem they cant help?  I am absolutely stuck and could really use help..if anyone has an idea id appreciate it.  I tried to follow the step by step instructions I couldnt even establish a connection to Firefox....As for now, im stuck paying for a machine I cant use.  :confused::(

---

### Post by mips on 2008-08-07
Well I have tried. I asked for some info and suggested some configs to do but got no feedback on these. We need a response from you in order to see what is going on and to localise the problem.

Right now I'm telling you your PC does not have a valid IP config and you will not get anywhere unless you sort that out first.

Hope you come right.

Edit: If you are having dificulties getting the info here then pipe the output to a text file.
Example, **ifconfig eth0 > output.txt**
to append the output of the second and other command to that text file so it does not get overwritten do:
 **ping 192.168.0.1 >> output.txt**
The >> basically means append to the file and dont overwrite.

You will now have a file called output.txt that you can easily move between computers with a flash key, floppy or cd.

---

### Post by sports fan Matt on 2008-08-07
I will go get some blank cd's to try and copy the info over..no guarantees there..I'll be back, thanks for the help:)

---

### Post by sports fan Matt on 2008-08-07
I will attempt from the windows machine to at least get to the regrestration part first so at least I can register then I will post the commands, save it to the blank cd then post the outputs

---

### Post by fedex1993 on 2008-08-07
go to 192.168.1.0 and see if the router page comes up. I am running on ATT dsl which is the same as sbc yahoo dsl and it works fine for me. Do you have a rj 11 or rj 45 cable coming into the back of the modem?

---

### Post by mips on 2008-08-08
> **fedex1993 said:**
> go to 192.168.1.0 and see if the router page comes up. I am running on ATT dsl which is the same as sbc yahoo dsl and it works fine for me. Do you have a rj 11 or rj 45 cable coming into the back of the modem?
> 
4.  destination 169.254.0.0 genmask 255.255.0


He cannot go to 192.168.0.1 because he does not have a valid IP config on his PC.

---

### Post by timcredible on 2008-08-08
the router should be giving your pc an ip address no matter what (after all, that's how the windows program they give you works - it connects to the router via ip).  if it's not doing that, then the router is broke, or you have the router plugged into the wrong port.  as for sbc not supporting linux, that's ok, neither does verizon.  just make them tell you your ppoe username and password.  you'll have to use firefox to connect to 192.168.0.1 and plug in that ppoe username and password in the ppoe section (not sure about 2wire routers, but shouldn't be too tough to find).  so now, the only other obstacle is, what is the default username/password to get into the router?  do a google search on your router brand/type, should find it.

---

### Post by hvac3901 on 2008-08-08
you should be able to access your router settings by connecting hard wire, and typing "home" in the address bar. (2-wire ?)

---

