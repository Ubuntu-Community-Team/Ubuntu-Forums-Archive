---
title: "HowTo: Easiest way to share files &amp; printers with Windows"
date: 2008-05-25
forum: Tutorials
---

### Post by netyire on 2008-05-25
[B][FONT=Trebuchet MS][SIZE=3]Justification and Notes
[/SIZE][/FONT][/B][FONT=Trebuchet MS][SIZE=3]- There are plenty of tutorials on the ubuntu forums that cover samba shares or printer sharing but I'll suppose that you want the fastest, easiest, least troublesome method to share files and printers with windows
- I'll attempt to provide the simplest method to do so in this guide
- For convention sake (rules for publishing a tutorial), author declares that no support is guaranteed.
[/SIZE][/FONT][B][FONT=Trebuchet MS][SIZE=3]
Assumptions

[/SIZE][/FONT][/B][FONT=Trebuchet MS][SIZE=3]- You want to share files & printers quickly and easily in a home environment
- You've got a firewall which blocks everything save the ip addresses of the computers you want to share files with and a couple of other required services

[B]Sharing Files
[/B]_*Linux*_
- Open a terminal & enter &quot;sudo apt-get install samba&quot; without the brackets
- In the same terminal type &quot;sudo gedit /etc/samba/smb.conf&quot;
- For the following step set WORKGROUPNAME to the workgroup defined under the windows computer (Right click My Computer and select properties under windows to access the workgroup name under the 'Computer Name' tab)
- Paste the following into the file, but edit the stuff in CAPS
```

[global]
   workgroup = WORKGROUPNAME
   server string = COMPUTERDESCRIPTION
   security = share
[Shared]
path = /home/USERNAME/FOLDER
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
create mask = 0777
directory mask = 0777
```[/SIZE][/FONT]```


```[FONT=Trebuchet MS][SIZE=3]
- In the same terminal enter &quot;sudo chmod 777 -R /home/USERNAME/FOLDER&quot; or whatever path you set above
- Finally enter &quot;sudo /etc/init.d/samba restart&quot; in the same terminal

[U][I]Windows XP
[/I][/U]- Open My Computer, click tools->map network drive
- Enter &quot;\\LINUXIPADDRESS\Shared&quot; in 'Folder' box and select an unused drive letter
- Click 'Finish'

[B]Sharing Printers
[/B]_*Linux*_
- Click System->Adminstration->Printing (On the same menu as your 'start' bar or application launch bar)
- Setup your printer
- Select 'Share Published Printers Connected To This System' under 'Server Settings'

[U][I]Windows XP
[/I][/U]- Enter &quot;LINUXIPADDRESS:631/printers&quot; in Internet Explorer or compatible web browser
- Mouseover the big printer name and copy the text in the status bar, or if you're using IE right click -> properties and copy the link address. In firefox, you can right click -> copy link location
- Start the 'Add new printer wizard' under printers & faxes in the control panel
- Select 'Network Printer' and click next
- Choose 'Connect to this printer' and paste the stuff you copied just now
- Select the driver for the printer (install it from disc) or choose a generic 'color printer'
- Click 'Finish' to complete the wizard

[B]Resources
[/B]- [http://www.debuntu.org/guest-file-sharing-with-samba](http://www.debuntu.org/guest-file-sharing-with-samba)
- Ubuntu Forums

[B]Remarks
[/B]- Please tell me how it turned out!
[/SIZE][/FONT]

---

### Post by neill on 2008-06-04
hi

i get an 'error 403 - forbidden' when i enter 192.168.1.1:631/printers

why might that be ??

ta

/neill

---

### Post by miciurin on 2008-06-05
Thank you very much. I tried to share the printer before with zero success. I followed your guide to the letter and it WORKS perfectly. I have just printed my first page from my XP laptop. On a secondary note, it will be useful for newbies to indicate where they can find the LINUXIP address. In my case (KUBUNTU) imoused over the plag icon (nera the clock and date) and that showed my kubuntu IP address.

Awesome.

---

### Post by netyire on 2008-06-05
Hi Neil! I think the problem may be with how the printers are setup. Click System->Administration->Printing and make sure that sharing of printers is allowed and that no restrictions are in place as to which users can access the printer. (Select the printer you wish to share and click on the access control tab)

Check if you have the right IP address first, open a terminal and enter sudo ifconfig /all
Then check if you can ping your linux box from windows, in windows click start->run type cmd and click run. Then type ping LINUXIPADDRESS. If you cannot ping the linux box this most probably means you have a firewall running. (Not sure which though). From here either add an exception if you know what firewall is running and how to go about doing that or install firestarter (hopefully the firewall is iptables, in which case you can use firestarter to reconfigure it), follow the setup instructions and add the WINDOWSIPADDRESS as an exception under the host section of the policy tab in Firestarter.

---

### Post by spinanicky on 2008-06-06
Is there a way to monitor how much each ip (or computer on the network) has printed. Basically I live with 3 house mates and want to be able to monitor how much each person has printed so that we can split the cost of a new cartridge among ourselfs depending on how much each person has printed...

Thanks 
Nicky

---

### Post by Rick K on 2008-06-13
If I understands this correctly, this assumes the printer is on the Linux box.  In my house (due to space concerns), the printer is on the XP machine.  Is there an easy and similar way to share printers in that config?

Thanks.

Rick

---

### Post by reswob on 2008-06-13
Anyone have any ideas about how to add a MAC OS X to this mix?

I have Ubuntu, XP and OS X (Tiger) at home and would like to share between all three.  So how do I set up Tiger?

Thanks

Craig

---

### Post by deeaycee on 2008-06-13
WOW!! This worked GREAT! Simple and quick. I'm running Xubuntu, XP, XP, Ubuntu and PCOS. I gave up long ago trying to share files with my XPs and this worked perfectly. Thanks

---

### Post by Vistaus on 2008-06-14
Thank you so much :D I tried so hard and searched all over the internet, but it was just this easy :O Ubuntu recognised the printers automatically, so I could print with Ubuntu for weeks. But Windows was a pity.

Only 1 question: How can you choose between color and black/white on Windows?

---

### Post by Vistaus on 2008-06-14
> **spinanicky said:**
> Is there a way to monitor how much each ip (or computer on the network) has printed. Basically I live with 3 house mates and want to be able to monitor how much each person has printed so that we can split the cost of a new cartridge among ourselfs depending on how much each person has printed...

Thanks 
Nicky

Install Webmin on your Linux machine ;)

---

### Post by caissyd on 2008-06-14
Hey guys,

I am able to share files between Windows XP and Ubuntu, but it's quite slow. I have a wired Gigabit network but copying files takes more time than if I were to FTP them... Any idea why it is so slow? 

Also, if I copy 10 images for example, it may only succeed in copying the first four ones before it gives me an error.

Firewall and Anti-virus have been deactivated, but nothing as changed...

Thanks

---

### Post by fredscripts on 2008-06-15
```
[B]Sharing Printers
[/B]_*Linux*_
- Click System->Adminstration->Printing (On the same menu as your 'start' bar or application launch bar)
- **Setup your printer**
- Select 'Share Published Printers Connected To This System' under 'Server Settings'

```


Sorry for newbie question, but how I setup my printer inside Printer Configuration - localhost window? I don't see any printer name nor something similar.

Thanks in advance!

Edit: I'm attaching a screen shot of the window:

---

### Post by fredscripts on 2008-06-15
Anyone? :( I'm sure it must be a newbie stuff and I'd really love to get the windows xp printer linked to my Ubuntu machine.

---

### Post by Vistaus on 2008-06-15
Click on the New Printer button ;)

---

### Post by fredscripts on 2008-06-15
Thanks for answering!!!

I've done it but still appears some kind of configuration I don't understand (I attach image)

What I should select?

Thanks in advance!!!

Edit: Ok I've gone further and selected Windows printer with Samba and then I found the name of my windows Xp computer there and selected it, hope I can go on with the tutorial :)

---

### Post by fredscripts on 2008-06-15
I've finished the tutorial (I think I did all the right way) but when printing from Ubuntu nothing happens , the file isn't printed nor any kind of error is raised :( even though I see the printer I have just in theory set up (I attach image).

Anyone knows why? :(

---

### Post by fredscripts on 2008-06-15
Sorry for bumping but...any command to know if I followed the tutorial well? I mean some kind of "ping" to the printer I have theoretically linked from the win xp machine to the ubuntu machine?

Thanks! At least I got perfectly running the tool to share files , which is so cool :)

---

### Post by Dave Warner on 2008-06-15
xlnt HOWTO!  One question: My Ubuntu boxes get their IP's via DHCP served from an XP SP3 box; how do I account for the changeable IP addresses?

---

### Post by Gyzome on 2008-06-17
> **fredscripts said:**
> Sorry for bumping but...any command to know if I followed the tutorial well? I mean some kind of "ping" to the printer I have theoretically linked from the win xp machine to the ubuntu machine?

Thanks! At least I got perfectly running the tool to share files , which is so cool :)

Simply print a empty page from Windows and Ubuntu. This way you won't waste any paper or ink and you know if your printer connection is ok. =D

---

### Post by garethsimpsonuk on 2008-06-17
Has an angel just sent this down to me as a gift?! 
I've been trying to get samba working on a homeserver for 2 months with no success. This quick n dirty method will do me for now till I can tighten up the security. 
I tried to reinstall windows home server ( also tried w2k3 + xp ) and the box just wont boot them ( linux cd's work fine... i think my box is giving me a hint )
Anyway thanx for this guide this will help. One thing is though in the guide linked to above it says 'this way is read only' I want to write from 4 / 5 different boxes and if this how to is based on the 1 on 'debuntu' then this is read only to.
Can anyone tell me how to make it read / write. is it chmod 777?
Also how I can i tighten this up as I will be running wan accesiible apps such as torrentflux and jinzoora.
Thanks again, I was very close to admiting defeat,

Gareth

---

### Post by Fejker on 2008-06-17
I've got a problem with my Samba shares. I was playing around with Webmin and screwed up my Samba config.
It used to work just fine but I wanted to add write support to some shares and I messed up.

I can get Samba to work with a guest user account but that's not secure at all. If I turn the guest access off it won't even let me connect to the Ubuntu box.

Connecting Windows Vista to Ubuntu Server Edition 8.04. It used to work before I started messing around with the configuration through Webmin. (I know, a dumb thing to do, but I needed write access)

Can someone please help me? Is there any way to reset the samba configuration? I tried removing and reinstalling samba but the config stays the same. And I also think that my home directory has messed up permissions.

PS: I followed this guide but it doesn't solve anything.

---

### Post by R_U_Q_R_U on 2008-06-25
[SIZE=4][netyire]("http://ubuntuforums.org/member.php?u=209967")

Thanks so much for this the tutorial. It is the easiest share procedure that actually works![/SIZE]

---

### Post by djgrant on 2008-07-03
So I guess this printing method just uses CUPS without Samba? Never knew it could do that.

So I guess I can make my smb.conf totally different for my shares and the printing will still work.

---

### Post by mdionne81 on 2008-08-04
This article worked flawlessly, thank you.  The only issue I had was not having the driver available but since it was already installed I just went to the new printers Properties -> Advanced in Windows and changed the driver.

---

### Post by RgnKjnVA on 2008-08-05
My windows machine rebooted and now it doesn't connect to my ubuntu machine. I've restarted the Samba daemons on my Linux box but no connection. I was all set to celebrate too, it was working like a champ. =o(  Why would rebooting completely derail connectivity?

---

### Post by netyire on 2008-08-05
Hi RgnKjnVA, try performing this step again:

[FONT=Trebuchet MS][SIZE=3][U][I]Windows XP
[/I][/U]- Open My Computer, click tools->map network drive
- Enter "\\LINUXIPADDRESS\Shared" in 'Folder' box and select an unused drive letter
- Click 'Finish'

[/SIZE][/FONT]If you don't want to keep on performing this step everytime you reboot, try checking reconnect at logon.[FONT=Trebuchet MS][SIZE=3]
[/SIZE][/FONT]

---

### Post by RgnKjnVA on 2008-08-05
False alarm, the XP didn't have connectivity to anything. It came back after a bounce. I'm backing up my music as I type, thanks!

---

### Post by idlefrog on 2008-08-12
I have Ubuntu (Hardy) running on my desktop which is wired to my wireless modem router. I have a Brother laser printer connected to this desktop via USB.

I also have two laptops in the house (one with Windows XP & the other with Vista) which connect wirelessly to the router. I am trying to get these to access the printer via the desktop. I had this working fine when I had XP on the desktop. I have followed the how to instructions but I hit a snag when entering the IP address in the browser in windows. The IP address of the desktop is 198.162.0.40, so I entered 192.168.0.40:631/printers in to IE on both laptops and neither laptop returned a webpage. I can ping the desktop from the laptop OK.

The printer is published and shared and internet printing is enabled.

Any suggestions very welcome.

---

### Post by Bob Heap on 2008-08-25
Thank you for a great Howto.
Did'nt work as I expected but it works, (I guess I fumbled a few things.)

---

### Post by Bapu on 2009-05-19
I do not want file sharing just yet. 

I do want printer sharing.

Do I need to install samba?

I have a Windows guest via VirtualBox on my Ubuntu 8.10 install. From within my Windows guest when I ping the actual IP address of Ubuntu, I get timeouts. Form that same Windows guest I can ping all other IP addresses (Windows boxes) on the subnet. Ubuntu and Windows are all on the same subnet (i.e. 191.167.33.x). Can anyone explain why I cannot ping Ububtu from Windows?

---

### Post by goggle5 on 2010-02-04
Great - got it up & running on the 1st try!  


Thanks!

---

### Post by tkoco on 2010-03-05
> **Dave Warner said:**
> xlnt HOWTO!  One question: My Ubuntu boxes get their IP's via DHCP served from an XP SP3 box; how do I account for the changeable IP addresses?

You need an Alias IP. Follow this tutorial:

[http://ubuntuforums.org/showthread.php?t=1259634&highlight=alias+netmanager](http://ubuntuforums.org/showthread.php?t=1259634&highlight=alias+netmanager)

And it works with 9.10

---

### Post by bigtel on 2010-03-09
I have to say that was the easiest set up I have ever done - all working great first time :D- thanks.

---

### Post by eric49a on 2010-03-28
ok i followed this guide very closely. when i get to the map network drive part i get a error that says "The network path \\172.16.1.65\Shared could not be found". i don't know what to do. i kinda need this file sharing. im running windows xp service pack 2 with no Internet connection, and Ubuntu 9.10 with a wireless Internet connection. The two computers a connected together through a switch with Ethernet cable. Any help would be great

---

### Post by bigtel on 2010-10-09
Is this method of sharing secure? Can the computer user next door now see my drive?

---

### Post by userm3 on 2010-10-23
make sure you unstall windows live assitant log in.  I shared it throw samba and it kept asking me for password even though i set the password off in windows.  uninstalling windows live assitant in windows should allow your ubuntu to share printer through windows.

---

### Post by eddacker on 2011-01-15
thanks for that, linux:windows, so many little things can go wrong.

---

### Post by eddacker on 2011-01-15
thanks for that tip, windows live does get a bit pushy at times.

---

### Post by rewritable on 2011-10-28
ha ha, i am not sure if i did the tutorial right but anyway its working 100% for me thanks i guess XD

---

