---
title: "Howto: configure cups on Ubuntu Server from command line"
date: 2006-08-20
forum: Server Platforms
---

### Post by ethridgt on 2006-08-20
I recently installed Ubuntu server on one of my machines at home.  I didn't want to install the Gnome desktop, so when it came time to configure cups as a print server I had a time figuring it out.  Nobody seems to be configuring from the command line, but without  Gnome, there doesn't appear to be another way (cups web page doesn't allow administration, details below).

I'm posting my notes here in the hope that it will save somebody else some frustration.  The guide below sets up cups on a server running a fresh install of Ubuntu Server 6.06.  The printer will be available to any computer on the network.

I use "smithers" as the hostname for my linux box.  You can substitute the IP address for "smithers" in the guide.

To install on smithers (my Ubuntu server):

1. $ sudo apt-get install cupsys cupsys-client

2. Modify /etc/cups/cupsd.conf

   - comment out
        #BrowseAllow @LOCAL
        #BrowseAddress @LOCAL
   - add
        BrowseAllow all

   - For the <Location /> block change "Allow localhost"
     to "Allow all".

        NOTE: If you do this for the other two location
              blocks, you can view the admin and config
              stuff.  However, the https stuff doesn't
              work so you can't administer anything.  You
              have to administrate from the command line.
              for more details as to why you can't do this
              from the web interface, which would be my first
              choice, check out /usr/share/doc/cupsys/README.Debian.gz.


3. Modify /etc/cups/cups.d/browse.conf

   - Change to "Browsing on"

4. Modify /etc/cups/cups.d/ports.conf

  - Change "Listen localhost:631" to "Listen 631"


5. $ sudo /etc/init.d/cupsys restart

6. Get info on the connected printers:
        $ lpinfo -v
        network socket
        direct usb://hp/deskjet%205550?serial=MY25K1K0TC2L
        network http
        network ipp
        network lpd
        direct parallel:/dev/lp0

7. Add the printer:
        $ sudo lpadmin -E -p hp5550 -v usb://hp/deskjet%205550?serial=MY25K1K0TC2L -P /usr/share/ppd/cups-included/HP/deskjet.ppd -u allow:all

NOTE: substitute my details for your details.  You can name the printer anything you like.  I don't think it allows numbers as the first letter, spaces, dashes, or underscore characters.  I'm not positive about these rules, so if I'm wrong, post a follow up.  :-)  As for the ppd file, there are only a few that come with cups, but I believe they cover the vast majority of printers.  Just take a guess and try the one you think will apply.  I think there were only 5 or so files.

8. To delete a printer (shouldn't need to do this):
        $ sudo lpadmin -x hp5550

NOTE: you shouldn't need to do this, but I included this just in case you wanted to remove a printer.

9. To set the default printer:
        $ sudo lpadmin -d hp5550

10. Enable the printer (required):
        $ cupsenable hp5550

11. Start accepting jobs (required):
        $ accept hp5550

NOTE: I read that the "-E" option is the same as the cupsenable and accept commands.  However, it didn't work for me.  I had to issue both commands before it would work.  You can check the status of the printer using the "printers" link below to see the printer status.

12. You can now browse the server using a web browser on
  port 631.  For example: [http://smiters:631](http://smiters:631).  To see the
  printers, navigate to [http://smithers:631/printers](http://smithers:631/printers)

13. To allow Windows XP to print to the cups printer, use the
  add printer wizard.  Start->Printers and Faxes.  Then
  select add printer.  Select network printer.  For the IP
  address use: [http://smithers:631/printers/hp5550](http://smithers:631/printers/hp5550).  Click
  next, find the appropriate driver.  Continue until wizard
  is complete.  Print a test page.  Enjoy!

---

### Post by wbc1228 on 2006-09-04
thanks ethridgt for the informative guide.
I was able to get my printer working under Xubuntu.

---

### Post by froggay on 2006-09-11
thanks a lot !

exactly what i was looking for .

Im' trying to add a cups-pdf printer but i can't find the generic poscript driver.ppd (i've seen it on 4.1)

does someone have already successfully configured cups-pdf on ubuntu server ?

---

### Post by TiredBird on 2006-09-12
Thanks a lot. I can't believe you figured that all out.

I wanted CUPS on my server but I didn't want to install a GUI to get it. Thanks to you my Lexmark E232 is now running on my headless server. I installed CUPS and configured the printer entirely through ssh from my laptop.

Now if I could just get my laptop (running Ubuntu Dapper Desktop) to print to CUPS on the server, I would be in hog heaven.

BTW, I think I have the answer to the -E question. According to the man pages for lpadmin when the -E precedes the -p it has a different meaning - it causes the conversation with the server to be encrypted.

---

### Post by metalhippyrich on 2006-09-13
I did manage to add a new printer using the web interface on a remote machine.

Thanks for your invaluable help; I followed the instructions above and got access to the administration page.  However I could not apply any changes as it failed password authentication.

I resolved this with:

adduser cupsys shadow

which allows the cups demon to read the shadow password file (as explained at the end of the the readme to which you referred:
/usr/share/doc/cupsys/README.Debian.gz  )

I could then add a new printer using the remote web interface rather than having to use the command line.

However, when I tried to change the server settings it completely replaced the cupsd.conf file, resetting all the "allow all" settings back to "allow @LOCAL" and locked me out.  (I wasn't very impressed with that).

---

### Post by maxwas on 2006-09-13
:evil: 

I have spent a whole day (solid) trying to get my epson stylus working with ubuntu server... i am now very mad.

I have followed this excellent guide, everything seems to be ok, when i get to...
> lpadmin -E -p epson -v usb://my details here...
the system hangs in mid air until i ctrl-c to stop it.

I have also added user cupsys shadow and myself to lpadmin and tried the web interface, still no joy.

I am getting *very* Pissed off now

david

---

### Post by memm on 2006-09-25
david,

i had the same problem but doing a
$ man lpadmin
says
...
 -v "device-uri"
...
That is, you must place quotation marks around the device-uri. 

So, your command should be like
$ lpadmin -E -p epson -v "usb://my details here..."

---

### Post by whittycat on 2006-09-28
I found this helpful but I still can't print. I have Kubuntu Breezy (at least that is what it was when I installed it; I have done apt-get update and apt-get upgrade but otherwise left it alone) with kernel 2.6.12. I can ping localhost and 127.0.0.1 and '# ping murgatroyd' works (murgatroyd is the hostname). ifconfig shows lo working ok. Firefox is ok.  The routing table looks ok but there is no entry for 127.0.0.1 is that right? If I add one it disappears at the next restart. '# ps ax | grep cups' returns '/usr/sbin/cupsd -F' which looks ok. '# /etc/init.d/cups restart' returns 'restarted scheduler'. The file /etc/hosts has (among others)

127.0.0.1   localhost
127.0.0.1   murgatroyd

However '# lpinfo -v' returns

'Unable to connect to server; connection refused'. 

In KDE if I look at System Settings -> Printers I get the sound of breaking glass and 'Connection to CUPS server failed'. 

Where am I going wrong? Any clue much appreciated. 

whittycat

---

### Post by ejstacey on 2006-09-28
This is exactly the information I was looking for!

Thanks much for all of this.

---

### Post by metalhippyrich on 2006-12-05
I have posted the following detailed and updated HOWTO:

HOWTO: Setup A Headless Ubunutu CUPS Print-Server
[www.ubuntuforums.org/showthread.php?p=1831119](www.ubuntuforums.org/showthread.php?p=1831119)

which covers some extra issues and may be of use to people.  Thanks to ethridgt for the original post which got us going.

---

### Post by MadMedis on 2007-01-18
David:

I had the exact same problem and was able to resolve it like this:  remove the -E from the beginning of the line, and use the quotes like memm suggested.  Hope that helps!

---

### Post by oldHat on 2008-02-19
Well, it finally worked for me.  But not until I unplugged my Bluetooth dongle and plugged the printer into a different USB socket.

Thanks!

---

### Post by Pilkjaer on 2008-02-22
i have troubles with accessing 196.168.0.104:631
but i already Allow all and set Listen 631. browsing on :(

---

### Post by Pilkjaer on 2008-02-23
> **Pilkjaer said:**
> i have troubles with accessing 196.168.0.104:631
but i already Allow all and set Listen 631. browsing on :(
Strange, but changing "Listen 631" to  "Listen 196.168.0.104:631" solved the problem. 192.168.0.104 is IP of the Ubuntu box

---

### Post by Pilkjaer on 2008-02-23
i wonder, is it possible to set user name and password and use it for authentication while printing?
one more question, why while having "Allow all" i still can't access printer from outside the network? (had in mind using printer for printing from internet)
and the very last question, is it possible to make a script that will take a print all the files from the specified folder? (in case if i upload my file to via ftp and then server will print them)

---

### Post by 2GooD on 2008-02-28
Thanks ethridgt!

---

### Post by don lee on 2008-05-30
It is obvious you have a great command of the Ubuntu command line.  I'm envious.  I have recently updated to Hardy Heron from Gutsy...  Have a problem with step 7. "Add the printer".  My server printer is an Epson Stylus Inkjet C87 on a parallel cable which obviously differs from your HP deskjet on a usb cable.  Is there a different lpadmin option to add a parallel cable printer versus an usb cable printer?  Any assistance is greatly appreciated.  Thanks,  Don

---

