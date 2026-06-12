---
title: "my server was hacked!"
date: 2010-04-15
forum: Security
---

### Post by Lakeside5 on 2010-04-15
I just got this comment from a helpful person:  'You have a Perl script listening on port 10000. Any idea as to what it could be?

Dovecot is a POP/IMAP server. If you didn't install it yourself, you have a big reason to worry, it means someone got root on your server.'
Can someone tell me right now (I am freaking out!) what to do? should I turn my computer off? God knows what they are doing with my computer,  and I can't host my website now anyway, it won't let me go there OR load localhost.

---

### Post by OpSecShellshock on 2010-04-15
Reinstall. If there's damage, there won't be a reliable way to account for all of it. You may eventually be able to put together a realistic picture of what happened, but it would take a while and you'd still end up reinstalling. Might as well skip the tedious stuff.

After reinstalling, if you still want to run a server, just make sure you check the configurations in the web-facing application to make sure you aren't just throwing it out there with default settings, and also make sure not to allow remote administration.

---

### Post by Jive Turkey on 2010-04-15
I would do more investigation before taking any drastic action.  Dovecot could have been installed as a dependency of something else.  In the case that you were actually hacked you will best be able to investigate by loading a liveCD.  Can you restart the webserver service "sudo /etc/init.d/<webserverservicenamehere> restart"
This info might be helpful:
[LIST=1]
[*]were you using a strong password?
[*]were there any administration services running (ie VNC, ssh server, webmin, etc.)?
[*]what is the output of "sudo netstat -a | grep 10000 && sudo netstat -a | grep LISTEN" (not from liveCD)?
[/LIST]
In your situation I would want to know both *if and how* a breach occured, others might say just reinstall and stop worrying.  You might want to pull the network plug after checking the netstat command and look at /var/log/auth  too.  If you really were hacked it would benefit you and all of us to figure out how.

---

### Post by lisati on 2010-04-15
Something doesn't add up here: on my server it's not dovecot that uses port 10000, but webmin, and even that's only accessible on my local network.

---

### Post by Lakeside5 on 2010-04-15
Wow thanks guys for the quick response! This is what I got:


udp        0      0 *:10000                 *:*                                
tcp        0      0 *:imaps                 *:*                     LISTEN     
tcp        0      0 *:pop3s                 *:*                     LISTEN     
tcp        0      0 localhost:mysql         *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:pop3                  *:*                     LISTEN     
tcp        0      0 *:imap2                 *:*                     LISTEN     
tcp        0      0 *:www                   *:*                     LISTEN     
tcp        0      0 *:webmin                *:*                     LISTEN     
tcp        0      0 ubuntu.local:domain     *:*                     LISTEN     
tcp        0      0 localhost:domain        *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:3128                  *:*                     LISTEN     
tcp        0      0 localhost:postgresql    *:*                     LISTEN     
tcp        0      0 localhost:953           *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp6       0      0 [::]:8009               [::]:*                  LISTEN     
tcp6       0      0 [::]:http-alt           [::]:*                  LISTEN     
tcp6       0      0 [::]:domain             [::]:*                  LISTEN     
tcp6       0      0 localhost:953           [::]:*                  LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     15104    /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     16740    /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     17756    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     18395    /tmp/keyring-mmaleT/socket
unix  2      [ ACC ]     STREAM     LISTENING     18401    /tmp/keyring-mmaleT/ssh
unix  2      [ ACC ]     STREAM     LISTENING     18407    /tmp/keyring-mmaleT/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     18650    /tmp/seahorse-8OvG1S/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     18680    /tmp/.ICE-unix/5985
unix  2      [ ACC ]     STREAM     LISTENING     18694    /tmp/orbit-bosslady/linc-17a2-0-d5e8c35939e3
unix  2      [ ACC ]     STREAM     LISTENING     18944    /tmp/orbit-bosslady/linc-1761-0-7cfc3514b96f2
unix  2      [ ACC ]     STREAM     LISTENING     19087    /tmp/orbit-bosslady/linc-17a8-0-75082b9ee2e15
unix  2      [ ACC ]     STREAM     LISTENING     19173    /tmp/orbit-bosslady/linc-17a9-0-55b1696040cbf
unix  2      [ ACC ]     STREAM     LISTENING     14878    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     19743    /tmp/orbit-bosslady/linc-17c0-0-275bdbe0af495
unix  2      [ ACC ]     STREAM     LISTENING     17695    /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     18622    @/tmp/dbus-TaJZ3sx5s1
unix  2      [ ACC ]     STREAM     LISTENING     21046    /tmp/orbit-bosslady/linc-179f-0-773a1c1fdbf73
unix  2      [ ACC ]     STREAM     LISTENING     26197    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     26201    /tmp/pulse-bosslady/native
unix  2      [ ACC ]     STREAM     LISTENING     26242    /tmp/orbit-bosslady/linc-17d6-0-512fd552ad7ef
unix  2      [ ACC ]     STREAM     LISTENING     26337    /tmp/orbit-bosslady/linc-17ca-0-775f601d88586
unix  2      [ ACC ]     STREAM     LISTENING     26404    /tmp/orbit-bosslady/linc-17e1-0-6253d97275c5a
unix  2      [ ACC ]     STREAM     LISTENING     26575    /tmp/orbit-bosslady/linc-17f6-0-19e04c27a4713
unix  2      [ ACC ]     STREAM     LISTENING     26682    /tmp/orbit-bosslady/linc-1802-0-65a4c14c63e0
unix  2      [ ACC ]     STREAM     LISTENING     27369    /tmp/orbit-bosslady/linc-183f-0-25f227bac1a0f
unix  2      [ ACC ]     STREAM     LISTENING     27453    /tmp/orbit-bosslady/linc-183c-0-6ea549c1da4e9
unix  2      [ ACC ]     STREAM     LISTENING     27484    /tmp/orbit-bosslady/linc-1836-0-3155e1adf08be
unix  2      [ ACC ]     STREAM     LISTENING     27536    /tmp/orbit-bosslady/linc-1834-0-64f40be863a5a
unix  2      [ ACC ]     STREAM     LISTENING     27513    /tmp/orbit-bosslady/linc-1842-0-18f4c918a4036
unix  2      [ ACC ]     STREAM     LISTENING     27634    /tmp/orbit-bosslady/linc-1857-0-131145f7221f
unix  2      [ ACC ]     STREAM     LISTENING     27752    /tmp/orbit-bosslady/linc-185e-0-6e3d60b2da657
unix  2      [ ACC ]     STREAM     LISTENING     29195    /tmp/orbit-bosslady/linc-1906-0-10c02fbb89034
unix  2      [ ACC ]     STREAM     LISTENING     166246   /tmp/orbit-bosslady/linc-5166-0-9981e44f1efc
unix  2      [ ACC ]     STREAM     LISTENING     82106    /tmp/orbit-bosslady/linc-35f7-0-4da6e9c17913
unix  2      [ ACC ]     STREAM     LISTENING     17513    @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     241630   /tmp/orbit-bosslady/linc-6bde-0-7ef51e0c6e8e9
unix  2      [ ACC ]     STREAM     LISTENING     174095   /tmp/orbit-bosslady/linc-538b-0-6dca80dca9857
unix  2      [ ACC ]     STREAM     LISTENING     17755    @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     17509    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     16742    /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     16808    @/var/run/hald/dbus-l47cksY1Dk
unix  2      [ ACC ]     STREAM     LISTENING     90999    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     16795    /var/run/dovecot/dict-server
unix  2      [ ACC ]     STREAM     LISTENING     16797    /var/run/dovecot/login/default
unix  2      [ ACC ]     STREAM     LISTENING     16802    /var/run/dovecot/auth-worker.5400
unix  2      [ ACC ]     STREAM     LISTENING     16835    @/var/run/hald/dbus-uSVwX0pAku
unix  2      [ ACC ]     STREAM     LISTENING     16070    /var/run/postgresql/.s.PGSQL.5432
unix  2      [ ACC ]     STREAM     LISTENING     14545    /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     14834    /var/run/dbus/system_bus_socket
 Jive Turkey I hear what you're saying (believe me I really don't feel like re-installing, it was hard for me to do it in the first place but......)
There are so many weird folders and files that I KNOW are new, and they all say I don't have permission to delete them and it is a lot of work to do that in the terminal, and then I won't know if I got them all.

---

### Post by Jive Turkey on 2010-04-15
I saw your other thread about having GIMP open when you woke up with a drawing having been started not by you.  Unfortunately I'm not really qualified to be of much help with the postmortem on this.  This is probably going to end with a reinstall.  Some other forumites may be able to help more.

I suggest you boot with a live CD and snnop through the dovecot configs and all of the logs.  If you aren't sure what you are looking at you might consider just reinstalling.  My curiosity wants to find if it was a 0day exploit or just weak security config but I doubt either of us have time to figure it out.

---

### Post by theozzlives on 2010-04-15
Set up iptables and close the ports you don't use.

---

### Post by HermanAB on 2010-04-16
Howdy,

Webmin listens on port 10,000.

Provided that you use decent passwords on ***ALL*** accounts and you do not install VNC, your system will be secure.

---

### Post by cdenley on 2010-04-16
That netstat output sucks. Use this command
```

sudo netstat -tulnp

```

That will list all listening TCP or UDP ports with numeric port numbers and the process name. Also, post output with "CODE" tags.
[NOPARSE]
```

output goes here

```
[/NOPARSE]

I believe webmin not only listens on TCP 10000, but also runs from a perl process. Did you install webmin? You shouldn't be installing stuff like webmin if you don't even know what port they listen on. Did you do a server install? If so, did you select the "mail server" box during install?

---

### Post by Lakeside5 on 2010-04-17
"That netstat output sucks"   LOL 

Unfortunately it won't let me do anything anymore, tried to enter your netstat command but I got this: ******y@ubuntu:~$ sudo -i
sudo: /var/run/sudo owned by uid 1000, should be uid 0
[sudo] password for*******: 
Sorry, try again.
[sudo] password for*****y: 
 ....I think I should re-install?  Might as well go with the total re-install, so what is the highest stable Ubuntu version without any known bad security problems?  Thanks.  Also, I had enough trouble installing the first one so I need a good guide I can download and transfer to my other computer (windows) and read.

*edit  I'm trying to see how much RAM I have to install Lucid Lynx (also wondering if I should install Lycid Lynx) and this it what the terminal shows:   total       used       free     shared    buffers     cached
Mem:           945        931         13          0         24        329
-/+ buffers/cache:        577        368
I'm not sure what that means, I thought it would show I had 200MB of ram, which is stil too little. Not sure what to do here.

---

### Post by Lakeside5 on 2010-04-17
@cdenley  yes I guess I am guilty of installing webmin and then at some point just sort of forgetting about it, I don't really use for some reason ( I think at some point I couldn't access it, it said my password was wrong) and I tried to get rid of the webmin folders but it wouldn't let me delete it.

I am going to wait until April 29 for the stable Lusty Lynx release, in the meantime read about it using my Windows computer, in the meantime not having this Ubuntu computer hooked to the internet (they can't use my server if it's not connected to the internet right?)  I will also read more about security and be more careful in the future!

---

### Post by mbuell on 2010-04-17
> **Lakeside5 said:**
> @cdenley  (they can't use my server if it's not connected to the internet right?)  

Fastest security in the world - pull the network plug - no doubt about it. 

Well, I'd guess this was an excellent learning experience for you - that was what you wanted when you got into this, right? :popcorn:

Anyway, you've certainly gained knowledge that you didn't have before. My vote goes for the "wipe the hard drive and reinstall" party to win this election.

While I have yet to figure out how to do it well myself, if I was doing p2p (other than bittorrent, and I hear that can be used now, too) I'd certainly want apparmor or selinux running. It's taken me a year to get comfortable enough using linux to really start the finer tuning of cracking down on security (outside of setting a moderately restrictive iptables policy). I'm still used to the Windows world, where I install a program and it does its thing and I rely on its reputation (and performance, i.e. good performance = no known infections). In Linux I have had to learn way more than I wanted to in the name of security. In the long run, this is not a bad thing, but I do get awfully grumpy about it from time to time.

---

### Post by ford_perfect on 2010-04-18
You could perform a remote vulnerability scan, there are some sites there which will do some scans for free - try with [http://www.think-security.com/scanner/](http://www.think-security.com/scanner/) and let us know what did it find out.

---

### Post by Lakeside5 on 2010-04-18
Thanks mbuell, I have learned that even Ubuntu hs 'vulnerbilities' lol  So should I wait for the stable Lusty Lynx release, or re-install the release before that, and then 'upgrade' later. I would really like to have my server back as I needed it to host my website which was a major college project due...two days ago lol. Hackers don't care what they do to people though.  @ ford_perfect: I tried to register there but it asks me for an account number when I register so I don't think it's free..

---

### Post by CharlesA on 2010-04-18
Wait about a month after the new release is live to do a clean install, so most of the problems will be ironed out.

The boards will be full of rage and discontent after Lynx goes live, happens after every new release.

---

### Post by iponeverything on 2010-04-18
```
sudo lsof |grep LISTEN
```

Can often tell you what is using what ports.

```

sudo lsof |grep TCP
sudo lsof |grep UDP

```

can give you useful data as well..

---

### Post by CharlesA on 2010-04-18
Nice commands there, thanks!

---

### Post by Lakeside5 on 2010-04-18
Charles that's too funny :)  Do you think I should install the stable release before Lusty Lynx, and then just update to Lusty?
@ iponeverything:  it's gotten so bad that I can't even do anything on the terminal as root (sudo)  It argues with me and seems to be saying (as in my earlier post) that someone else has control as root?  Even when I use sudo -i. That may be how this trouble started, as, after a long time of NOT just assigning myself to be root (sudo -i) I finally used it as it seemed to work better, and I assumed that once I closed the terminal, it went back to the default of not being assigned root permissions, but maybe that wasn't true.

---

### Post by cariboo on 2010-04-18
If you intend on running a server, it really doesn't matter if you have the latest version, unless there is a must have feature. The only thing I can see in the latest server version is more tools for cloud integration. Karmic will work just as well for you, and only install the servers you need. 

If you need a desktop manager, start it manually, and shut it down when you aren't using it. Don't use vnc for remote administration, instead use X-forwarding with ssh.

---

### Post by uRock on 2010-04-18
A clean install is the only way to remove the intruder's settings. Once you reinstall, I recommend using [Snort]("http://ubuntuforums.org/showpost.php?p=5786055&postcount=2") and/or [Ninja]("http://blog.bodhizazen.net/linux/how-to-ninja-ubuntu-10-04/") to protect your server.

---

### Post by bodhi.zazen on 2010-04-18
> **iponeverything said:**
> ```
sudo lsof |grep LISTEN
```Can often tell you what is using what ports.

```

sudo lsof |grep TCP
sudo lsof |grep UDP

```can give you useful data as well..

Try this one =)

```
sudo lsof -i -n -P 
```

You may also enjoy :

```
sudo netstat -ntulp
```

---

### Post by Lakeside5 on 2010-04-18
Thank you Cariboo907 and uRock,(and everyone else) that's good advice that I shall follow. Now..off to download Karmic. I don't want to wait weeks for the cd, and I don't have a disc burner, haven't had one for two years!  Can I just dld the code and install like that, (or I could see if a local store has a copy- that's where I got the Intrepid one).

---

### Post by CharlesA on 2010-04-18
You can boot (and install) Karmic off of usb. :)

It definitely sounds like the box is hosed and a reinstall is the only thing you can do to be sure that everything is clean.

---

### Post by Lakeside5 on 2010-04-18
So just to be sure here (cause I'm not so good at this) I can download onto my external hard drive and then just click on the download and take it from there?  I have all my files from 'Ubuntu' computer (the one that got hijacked- this one is the windows one) on my external hard drive and I don't want to lose them so I hope nothing happens to the external when I use it to install Ubuntu, but I don't think anything will.  Where is the best place to download Karmic to install that way? Every thing I read tells me to burn the disc and boot from it.

---

### Post by CharlesA on 2010-04-18
Erm, I should have been more clear. You can install Ubuntu off of a USB thumb drive. You can probably use unetbootin or something similar to put the iso on the thumb drive and make it bootable.

I think you can install it from a USB hard drive too, but I think it's a bit of a pain to do.

The way I do it now is that I use my multipass (USB stick made bootable with Grub4DOS)

---

### Post by Jive Turkey on 2010-04-18
It sounds like you need to get your project up and running.  Fiddling with alternate install methods will only bog you down.  If you still have the disk from last time you installed, that should work just fine.  Just make sure you install the latest updates right away.  Your school's computer lab probably has a CD burner if you really want the latest stable release.

Barring that, the ways I know to install without a CD are.
1. USB thumb drive
  not all computers can boot this way, especially older ones.
  Amount of time it would take Jive Turkey to set up 5-10 min with a  working ubuntu desktop, 3 hours on a windows machine.
2.  Network boot
   AFAIK you need a tftp server working to get this done
   Amount of time it would take Jive Turkey to set up 3 days to 3 weeks, possibly never if I can't find good documentation.
3.  Some crazy disk writing-file-copying-wackiness probably involving dd and radical partitioning scheme.
   I attempted this once with another distro and never really got decent results.  Would probably take me at least a week to figure it out, if ever unless I could find a really good howto.

---

### Post by uRock on 2010-04-18
[unetbootin]("http://unetbootin.sourceforge.net/") would be the easiest way to go.

---

### Post by Lakeside5 on 2010-04-19
Thanks so much to all of you..now ur gonna kill me :)  I got my hands on a Jaunty Jackelope disc and my disc player seems to work with it (didn't work with another disc I had, probably the disc was bad) so...now I'm wondering, do I have to uninstall the 'present Ubuntu that's in my computer (Intrepid Ibex, the server that was hijacked).  Or do I just install over top of it...I'm reading the install manual that is on the install disc but I'm not sure.  I gues when I'm ready I click on some file in the folder marked 'install'.

---

### Post by Lakeside5 on 2010-04-20
Ok, I backed up all my files on external drive, and I put my Jaunty Jackelope server installation disk in the cd drive, and I looked at all the folders it shows but I can't figure out which thing I click on to start the installation....and also I hope it overwrites the other installation...I took a screenshot if you want to see it.

---

### Post by uRock on 2010-04-20
The disk should boot into installation mode. When you get to the partitioner, select to format the partitions.

---

### Post by Hobgoblin on 2010-04-20
> **Lakeside5 said:**
> I can't figure out which thing I click on to start the installation....

You need to boot from the CD.

Is this the server edition or the desktop edition you have a CD for?

---

### Post by Lakeside5 on 2010-04-20
Hobgoblin, uRock:  Nothing happens when I pop the disk in, so I'm going to call the computer store where I go tit  aand ask about it.   It is the server edition.

---

### Post by CharlesA on 2010-04-20
Make sure that the boot order is set correctly and that it is infact booting from the CD.

You should get a menu that asks what you want to do.

---

### Post by Ko$ on 2010-04-20
I think the folder /var/log must become your friend ) The system writes everything it does. You don`t need to guess whether you were haked or not. 

Also, try to use logcheck. It will send you emails about all security events. it can do it daily or every hour.

p.s. reinstalling can`t be helpful.

---

### Post by cdenley on 2010-04-20
> **Ko$ said:**
> I think the folder /var/log must become your friend ) The system writes everything it does. You don`t need to guess whether you were haked or not.

Logs can confirm that you were hacked, but cannot confirm that you were not.

---

### Post by Ko$ on 2010-04-20
> **cdenley said:**
> Logs can confirm that you were hacked, but cannot confirm that you were not.

Of course ) just looking at, for example, auth.log you can find many interesting things such as bot-bruteforcing attacks on ssh port, which in the case (i think) was the problem. That warns you about passwords, etc.

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> I think the folder /var/log must become your friend ) The system writes everything it does. You don`t need to guess whether you were haked or not. 

Also, try to use logcheck. It will send you emails about all security events. it can do it daily or every hour.

p.s. reinstalling can`t be helpful.
It would be impossible to track down every change added by an intruder. The only way to be sure a hacked system can be trusted again is to reinstall ubuntu.

Lakeside5- You may have to hit ESC, F2 or F12 to get the system to boot from the disk.

---

### Post by Ko$ on 2010-04-20
> **uRock said:**
> It would be impossible to track down every change added by an intruder. The only way to be sure a hacked system can be trusted again is to reinstall ubuntu.

Lakeside5- You may have to hit ESC, F2 or F12 to get the system to boot from the disk.

You can also use your backups if you are not confident. It`s far not the only way.

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> You can also use your backups if you are not confident. It`s far not the only way.

He doesn't have backups. Reinstalling is simple and takes only 20-30 minutes with a decent Internet connection to get up and running install, then the OP would just have to get his/her data back onto the HDD.

---

### Post by Ko$ on 2010-04-20
> **uRock said:**
> He doesn't have backups. Reinstalling is simple and takes only 20-30 minutes with a decent Internet connection to get up and running install, then the OP would just have to get his/her data back onto the HDD.

how about configs and services you have? 

Sorry, maybe you`re right. 

It just sounds like windows-like-problem-solving ))

p.s. if you don`t have any backups of your server, than you probably shouldn`t run the server and give this work to anyone else. You have to do that.

pp.ss. # dd if=what_i_want_to_save of=where_i_want_to_save bs=1024  , simple.

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> how about configs and services you have? 

Sorry, maybe you`re right. 

It just sounds like windows-like-problem-solving ))

p.s. if you don`t have any backups of your server, than you probably shouldn`t run the server and give this work to anyone else. You have to do that.

pp.ss. # dd if=what_i_want_to_save of=where_i_want_to_save bs=1024  , simple.

What good are logs when they can easily be altered by the person who cracked the system?

---

### Post by Ko$ on 2010-04-20
> **uRock said:**
> What good are logs when they can easily be altered by the person who cracked the system?

well, he obviously wouldn`t get a root account directly and you will have some time to read the logs. Second thing is to brute the passwords from "shadow" which is not easy or fast I guess. Of course, if you have 12345 password you don`t need the logs :)

p.s. but it seems that he did change the root-password simply which is the most stupid thing you can do. So if he is not smart, then you will be able to restore your system because it`s most likely that he used "hack-tools" and there is no damage, that can`t be deleted.

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> well, he obviously wouldn`t get a root account directly and you will have some time to read the logs. Second thing is to brute the passwords from "shadow" which is not easy or fast I guess. Of course, if you have 12345 password you don`t need the logs :)

p.s. but it seems that he did change the root-password simply which is the most stupid thing you can do. So if he is not smart, then you will be able to restore your system because it`s most likely that he used "hack-tools" and there is no damage, that can`t be deleted.
From reading the OP's posts, the hacker was able to alter the sudoers file. It is imperative to read the whole thread, especially the OP's posts to get all of the info possible before giving advice.

---

### Post by norseman-has-a-laptop on 2010-04-20
[QUOTE= what to do? should I turn my computer off? God knows what they are doing with my computer.[/QUOTE]
unplug from the internet if your being hacked 

and i dont think your being hacked.
it could be something totally different in my opinion

---

### Post by cariboo on 2010-04-20
In a lot of cases, there may not be anything in the logs, the last rootkit I installed, didn't write anything to the logs, and it didn't show up when running rkhunter or chkrootkit. The only real indication was activity on a port I normally don't have open. In this case it was port 8001.

---

### Post by norseman-has-a-laptop on 2010-04-20
> **norseman-has-a-laptop said:**
> unplug from the internet if your being hacked 

and i dont think your being hacked.
it could be something totally different in my opinion

oops i messed up on my quote

---

### Post by bodhi.zazen on 2010-04-20
> **cariboo907 said:**
> In a lot of cases, there may not be anything in the logs, the last rootkit I installed, didn't write anything to the logs, and it didn't show up when running rkhunter or chkrootkit. The only real indication was activity on a port I normally don't have open. In this case it was port 8001.

+1

The rkhunter and chkrootkit tools are limited in that they only detect known rootkits. They do not help with unknowns or zero day exploits.

Also, crackers do not necessarily need root ...

---

### Post by Ko$ on 2010-04-20
> **cariboo907 said:**
> In a lot of cases, there may not be anything in the logs, the last rootkit I installed, didn't write anything to the logs, and it didn't show up when running rkhunter or chkrootkit. **The only real indication was activity on a port I normally don't have open**. In this case it was port 8001.

iptables logs? ))

---

### Post by Ko$ on 2010-04-20
> **uRock said:**
> From reading the OP's posts, **the hacker was able to alter the sudoers file**. It is imperative to read the whole thread, especially the OP's posts to get all of the info possible before giving advice.

he did that with nobody rights? or does it say that he is **a hacker**?

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> he did that with nobody rights? or does it say that he is **a hacker**?
Still haven't read all of the posts?

---

### Post by Ko$ on 2010-04-20
My advice to topic starter is more understanding and nothing more.

To change sudores file it`s the same as merely send an email to admin that the server was hacked. For me it`s so. May be I`m wrong. Sorry ))

---

### Post by Ko$ on 2010-04-20
> **uRock said:**
> Still haven't read all of the posts?

If you don`t know, you can use "su" command instead of sudo, and not yours but the root password and become root. 

What exactly do I have to read?)

---

### Post by bodhi.zazen on 2010-04-20
> **Ko$ said:**
> My advice to topic starter is more understanding and nothing more.

To change sudores file it`s the same as merely send an email to admin that the server was hacked. For me it`s so. May be I`m wrong. Sorry ))

You would think the OP would know if s/he changed the sudoers file so by definition the intruder has root access.

Personally I would not trust any binary file on a cracked computer and I would review all the data and if possible restore from a known good back up. 

Although one can sometimes clean a cracked box, installing is IMO easier, faster, and more reliable.

IMO the primary role of forensics is to determine and remedy the security flaw that allowed the intruder access. Obviously this can vary from physical access to unsecured servers to security holes etc.

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> iptables logs? ))
What does iptables keep a log of when not specifically instructed to keep logs, such as when a rule is created in GUFW and then logging can be turned on. Everyone I have asked has said that iptables doesn't log anything unless it is told to do so.

---

### Post by bodhi.zazen on 2010-04-20
> **Ko$ said:**
> If you don`t know, you can use "su" command instead of sudo, and not yours but the root password and become root. 

What exactly do I have to read?)

Not on a default installation of Ubuntu, the root account is locked.

---

### Post by Ko$ on 2010-04-20
> **bodhi.zazen said:**
> **You would think the OP would know** if s/he changed the sudoers file so by definition the intruder has root access.

Personally I would not trust any binary file on a cracked computer and I would review all the data and if possible restore from a known good back up. 

Although one can sometimes clean a cracked box, installing is IMO easier, faster, and more reliable.

IMO the primary role of forensics is to determine and remedy the security flaw that allowed the intruder access. Obviously this can vary from physical access to unsecured servers to security holes etc.

Well, that`s why he came here for help, isn`t? So, somehow he did that.

---

### Post by Ko$ on 2010-04-20
> **bodhi.zazen said:**
> Not on a default installation of Ubuntu, the root account is locked.

Default ) I hope the next time topic starter will know how to change that "default" issue:

> 
kos@lapserv:~$ su
Password: 
su: Authentication failure
kos@lapserv:~$ sudo -s
[sudo] password for kos: 
root@lapserv:~# passwd  # here i just set other password for root.

Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
root@lapserv:~# exit
exit
kos@lapserv:~$ su
Password: 
Added user root.

root@lapserv:/home/kos# 



It`s not difficult I guess.

---

### Post by cdenley on 2010-04-20
> **Ko$ said:**
> Default ) I hope the next time topic starter will know how to change that "default" issue:

Hopefully they will also read the stickies.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> Default ) I hope the next time topic starter will know how to change that "default" issue:



It`s not difficult I guess.
I would think that the OP would know what he/she has done if the OP went out of the way to learn those commands. I believe it is against the CoC to post that command set.

---

### Post by lisati on 2010-04-20
> **cdenley said:**
> Hopefully they will also read the stickies.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

... and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ko$ on 2010-04-20
> **uRock said:**
> I would think that the OP would know what he/she has done if the OP went out of the way to learn those commands. I believe it is against the CoC to post that command set.

Sorry ))) I`m a "newby", doesn`t know that it was against the rule. At the same time.. 

Can anyone explain why it "security issue" is that you can`t "use" root account?

---

### Post by lisati on 2010-04-20
> **Ko$ said:**
> Sorry ))) I`m a "newby", doesn`t know that it was against the rule. At the same time.. 

Can anyone explain why it "security issue" is that you can`t "use" root account?

See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ko$ on 2010-04-20
> **lisati said:**
> See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I didn`t ask how to use sudo, I asked why is it "dangerous" to use the root? Why is it a security problem? Or is it just for new users in order to prevent their "doings" on the root account?

---

### Post by uRock on 2010-04-20
> **Ko$ said:**
> I didn`t ask how to use sudo, I asked why is it "dangerous" to use the root? Why is it a security problem? Or is it just for new users in order to prevent their "doings" on the root account?
Did you bother reading the page? It clearly explains why the root account is a security hazard. It is the same concept that Windows uses when trying to deter people from using their admin account for everyday use. The root account is for administering the system. The root account is not needed because an administrator/owner can easily run commands with sudo when he/she needs to get something done. The OP claimed that he/she didn't always exit the sudo -i status, therefore leaving the possibility for a cracker to get in and easily have root access. Same reason applies for why someone would not want to use the root account.

---

### Post by philinux on 2010-04-20
> **Ko$ said:**
> I didn`t ask how to use sudo, I asked why is it "dangerous" to use the root? Why is it a security problem? Or is it just for new users in order to prevent their "doings" on the root account?

Please read the link provided above and also this one.

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Ko$ on 2010-04-20
Yea, I did bother. But the only things I`ve read are 1: you won`t forget your root password and 2: it will be impossible to brute root password (which you can set in any daemon) (ssh for example). So I`ve got my daemons without root-authentication, the question is: am I now secured? or there are other ways that the "no su" can help me? Sorry guys, I just wanna know why this is. I`ve google it, but it goes all about "forgetting password" and bruteforce.

---

### Post by mr-woof on 2010-04-20
When Cariboo mentioned installing the rootkit further up the thread, how did you find out it was installed? Using the netstat command?

---

### Post by norseman-has-a-laptop on 2010-04-20
one thing there are alot of admin/staff on this thread

---

### Post by d3v1150m471c on 2010-04-20
So someone was watching a service on a port...whoopity doo. Install psad and make sure your server is secure. Listening to a port doesn't indicate that you've been hacked.

---

### Post by conradin on 2010-04-20
My professional opinion is to unplug the computer immediately. Shutting down can allow scripts to remove or make changes that can erase their existence. Once shut down, remove the Hard Drive and copy it. Then work on the copy. DO NOT Restore from the hacked copy, hopefully you have a secure back up some place you can work on.

---

### Post by cariboo on 2010-04-20
I ran:

```
sudo netstat -tnlp
```

and looked through the output, in this case I found another instance of ssh running where it shouldn't.

---

### Post by norseman-has-a-laptop on 2010-04-21
i think everyone has said something about unpluging it lol

---

