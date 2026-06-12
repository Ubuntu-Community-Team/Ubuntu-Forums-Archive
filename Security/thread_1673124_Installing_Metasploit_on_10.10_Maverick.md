---
title: "Installing Metasploit on 10.10 Maverick"
date: 2011-01-21
forum: Security
---

### Post by k3n0bl on 2011-01-21
I know this might be a recycled topic,  but the instructions on [http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu) are outdated and flat out doesnt work.

Can someone point me to the easiest way to get this installed?  I know that with some tweaking it is possible to get the above instructions to work however,  I'm a noob and don't know the tweaking involved.

Thanks for any help!

I've seen  instructions for 10.4,  but they don't work either.

---

### Post by Deadboy420 on 2011-02-22
The trick is to first make it executable by typing:

```
sudo chmod +x framework-3.5.2-linux-i686.run

```then simply run:

```
sudo ./framework-3.5.2-linux-i686.run
```and follow the dialog. :-\"=D>

---

### Post by highspider on 2011-03-02
yeap above works perfect

And for Ubuntu Lucid, Maverick, ..ect 
 don't forget to  UPDATE THE EXPLOITS after install and every so often.

assuming you did default install to dir /opt/framework-3.5.2/msf3

```

sudo apt-get install subversion
cd /opt/framework-3.5.2/msf3
sudo svn update

...OUTPUT IS... 
U    test/functional/framework/msfconsole_spec.rb
U    test/functional/framework/msftest/psexec.msftest
...skip....
A    data/armitage/armitage
U    data/armitage/whatsnew.txt
A    data/wordlists/sap_common.txt
U    data/meterpreter/meterpreter.php
U    data/wmap/wmap_sample_profile.txt
Updated to revision 11868.

```:twisted:this hooks up all new exploits for fun and enjoyment :twisted:

```
msfconsole

       =[ metasploit v3.6.0-beta [core:3.6 api:1.0]
+ -- --=[ 647 exploits - 340 auxiliary
+ -- --=[ 216 payloads - 27 encoders - 8 nops
       =[ svn r11878 updated today (2011.03.04)

```

---

### Post by d0chaser on 2011-03-16
ty for the info :D

---

### Post by abdellatef1 on 2011-03-17
please my friend 

i've got framework-3.6.0-linux

When I write

sudo chmod +x framework-3.6.0-linux-i686.run

give me error please give explain video

chmod: cannot access `framework-3.6.0-linux-i686.run': No such file or directory

---

### Post by Leeming on 2011-03-17
> **abdellatef1 said:**
> please my friend 

i've got framework-3.6.0-linux

When I write

sudo chmod +x framework-3.6.0-linux-i686.run

give me error please give explain video

chmod: cannot access `framework-3.6.0-linux-i686.run': No such file or directory

Double check it exists (in the directory your in). I generally like using tab complete to confirm this.

Then when running, remember to do ./framework-3.6.0-linux-i686.run or what ever since '.' might not be in your path (read its recommended you dont add it either)

---

### Post by stlsaint on 2011-03-17
Yep from the above error you probably typed in the name wrong. Enter the directory where the object is and use the tab feature, oooorrrr just use GUI! :D

---

### Post by Dire_Devourer on 2011-03-20
I've come across similar threads by people saying that they cant launch the msfweb interface. If your experiencing that problem heres the reason why.

The msfweb interface has been phased out of the framework altogether!

The entire framework runs from within the newer Java based GUI, after you go installing the framework, you should follow this guide on the Metasploit Site about getting the framework going and use the subversion tool (svn command) to keep the framework current as it is updated almost on a daily basis.

The most current version of the framework at the time of writing this is:

=[ metasploit v3.7.0-dev [core:3.7 api:1.0]
=[ 655 exploits - 343 auxiliary
=[ 216 payloads - 27 encoders - 8 nops
=[ svn r12033 updated today (2011.03.20)

If your looking for details of how to set the framework up you should checkout this most excellent article over at the metasploit site which covers all aspects of getting it up and running on Ubuntu. The command ./framework-3.6.0-linux-i686.run does work if you have an i686 system but it does say very clearly in the read-me this install is based on using the Unix *.tar-ball.

[http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu](http://www.metasploit.com/redmine/projects/framework/wiki/Install_Ubuntu)

Hope that helps some of ya out.. TTFN

---

### Post by mujahied on 2011-07-11
> **abdellatef1 said:**
> please my friend 

i've got framework-3.6.0-linux

When I write

sudo chmod +x framework-3.6.0-linux-i686.run

give me error please give explain video

chmod: cannot access `framework-3.6.0-linux-i686.run': No such file or directory


please check if u are in the corect directory and the chmod 

Press Alt + F2 and type:
     Code:
     gksu nautilus /home/username/downloads

and then modify the permision manualy

---

