---
title: "Security update: Sun Java JRE update 17"
date: 2009-11-04
forum: Security
---

### Post by Pjotr123 on 2009-11-04
Sun has issued update 17 for Sun Java 6 JRE. This contains many security fixes: [http://java.sun.com/javase/6/webnotes/6u17.html](http://java.sun.com/javase/6/webnotes/6u17.html)

Users of Ubuntu 8.04 Hardy Heron will probably (in due time?) receive this update automatically, from the update function of Ubuntu itself. 

Users of other Ubuntu versions, including 9.10 Karmic Koala, will need to update manually. I've provided a how-to:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Regards, Pjotr.

---

### Post by Pjotr123 on 2009-11-05
Some people have reported problems with my how-to, when they already had installed an older version of JRE. So I've added an instruction to my JRE how-to, to remove the old version first:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Have fun! JRE is still much better than OpenJDK. :-)

---

### Post by DougieFresh4U on 2009-11-05
I went through all the steps and it failed. 
Here is as far as it gets:

```
dougie@dougies32bitter:~$ cd /opt
dougie@dougies32bitter:/opt$ sudo mkdir java
dougie@dougies32bitter:/opt$ cd java
dougie@dougies32bitter:/opt/java$ sudo mkdir 32
dougie@dougies32bitter:/opt/java$ sudo mv ~/jre-6u17-linux-i586.bin /opt/java/32
mv: cannot stat `/home/dougie/jre-6u17-linux-i586.bin': No such file or directory
dougie@dougies32bitter:/opt/java$ 
 
```
Any suggestions?

---

### Post by Pjotr123 on 2009-11-06
> **DougieFresh4U said:**
> I went through all the steps and it failed. 
Here is as far as it gets:

```
dougie@dougies32bitter:~$ cd /opt
dougie@dougies32bitter:/opt$ sudo mkdir java
dougie@dougies32bitter:/opt$ cd java
dougie@dougies32bitter:/opt/java$ sudo mkdir 32
dougie@dougies32bitter:/opt/java$ sudo mv ~/jre-6u17-linux-i586.bin /opt/java/32
mv: cannot stat `/home/dougie/jre-6u17-linux-i586.bin': No such file or directory
dougie@dougies32bitter:/opt/java$ 
 
```
Any suggestions?

You probably didn't do this:
"Store the file in your personal folder; don't leave it on your desktop. This will simplify the terminal commands that you'll execute later on."

Maybe that text is not clear enough. So I've amplified the text in the how-to as follows:
"***Note:*** Store the file straight in your personal folder; don't leave it on your desktop or in the folder Downloads. This will simplify the terminal commands that you'll execute later on.
For example: user John shouldn't leave the file in [COLOR="Blue"]/home/John/Desktop[/COLOR] or in [COLOR="Blue"]/home/John/Downloads[/COLOR], but should put it in [COLOR="Blue"]/home/John[/COLOR] instead."

---

### Post by Pjotr123 on 2009-11-10
It's a bit disconcerting, that there's still no sign of a JRE update for 8.04 Hardy Heron... That's an LTS version which should be protected.

I've reported this on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/477812](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/477812)

Feel fee to support this bug report there. :-)

Note: I repeat, that non-LTS-versions should be updated manually, without delay! For example by applying this how-to: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by MechaMechanism on 2009-11-10
How about a ppa for Sun Java or is that not allowed.

---

### Post by witeshark17 on 2009-11-10
Thanks, got it, previous issue must have been a tiny syntax error

---

### Post by PaulInBHC on 2009-11-10
Your instructions were clear and work fine for me. I did not have any java installed even though I thought I had done it before.
Thanks for the helpful webpages.

---

### Post by Soul-Sing on 2009-11-11
pjotr thx again. :)

---

### Post by quixote on 2009-11-12
Thank you!  I could have flailed around for weeks without that!

One hint I came across that I found useful when trying to follow detailed commands:  It's possible to copy the command on the web page using the usual Ctrl-C, and then paste it into the terminal at the prompt using **Shift-Ctrl-V**.  (You can also copy terminal commands by selecting with the mouse and using Shift-Ctrl-C.  Don't use Ctrl-C, for obvious reasons :D)  That's helped me prevent copying typos.

---

### Post by cobradevil on 2009-11-12
I also put a request in your ticket pjotr!

This one is important and i wil not install it manually because i think the distro should update.

With kind regards

William

---

### Post by Pjotr123 on 2009-11-12
> **cobradevil said:**
> I also put a request in your ticket pjotr!

This one is important and i wil not install it manually because i think the distro should update.

With kind regards

William

Thanks. :)

Well, I certainly hope they will update this package (JRE) in 8.04, but don't hold your breath... Generally Ubuntu is pretty quick with security fixes, but they have a very bad record for this particular package. 

I've been using JRE in Ubuntu for more than three years, and getting updates for it has always been an ongoing concern in all those years. Apparently they feel that we all should move to OpenJDK + IcedTea plugin... :-(

---

### Post by witeshark17 on 2009-11-12
Thanks again loads to the OP! I just had a thought that the future OS updates may begin to include this. Making the change by your 'how to' feels safer than waiting IMO. By the way, the Apple update came out today or maybe last night.

---

### Post by quixote on 2009-11-12
Not sure what I'm doing wrong, but I just can't get it to work in the following situation:

32-bit karmic running in virtualbox, namoroka 3.6beta2, installed as user, not sudo, under my ~/  

I installed java in /opt as in the instructions.  The symlink in ~/.mozilla/plugins is used by the default firefox (3.5), but was ignored by my non-sudo 3.6b2.  

I noticed it had its own plugins directory (~/namoroka/firefox/plugins/) so I put a symlink in there as well.  Still no joy.

And as for all of us using openjdk and icedtea -- I'd love to, except half the sites don't work right with those! :mad:

Thanks again for these great instructions.  As I say, works great with my default firefox 3.5.  It's just the installed-as-user 3.6 giving me grief.

---

### Post by mtecknology on 2009-11-18
I like to think that computers are multi-user. So... placing this in /opt would be the best idea.

I would however simplify the commands.

# As Root
mkdir -p /opt/java/66
mv ~/jre-6u17-linux-x64.bin /opt/java/64
chmod +x ~/jre-6u17-linux-x64.bin
/opt/java/64/jre-6u17-linux-x64.bin
  Do you agree to the above license terms? [yes or no]  yes
update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_17/bin/java" 1
update-alternatives --set java /opt/java/64/jre1.6.0_17/bin/java

# As User
mkdir ~/.mozilla/plugins
ln -sf /opt/java/64/jre1.6.0_17/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

# Note that ln -f forces so rm prior is not required
# This allows updates to require only a single command

Thanks very much for making this how-to. It made things work magically for me. Hence, why I feel the need to help you make it easier.

---

### Post by Coach_Mark on 2009-11-20
ok.  I have an HP dv6000 laptop with an AMD64 processor.  I am trying to install jre-6u17-linux-x64.bin.  I followed all the instructions.  But, after saying "yes" to the agreements, I got the following...

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
Extracting...
./install.sfx.5276: 1: ELF: not found
./install.sfx.5276: 2: Syntax error: ")" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.
mark@mark-laptop:/opt/java/64$ 


any ideas on where I went wrong or what happened?

---

### Post by Soul-Sing on 2009-11-20
two possibility's:
1) corrupt .binfile
2) run it with sudo "rights"/permission.

---

### Post by Pjotr123 on 2009-11-20
It's as leoquant says. Most probably possibility number one, i.e. a corrupt download from the Java website. 

Solution: delete your current downloaded JRE file and download another copy. Then delete /opt/java with all it's contents. Then repeat all steps, starting at the beginning.

---

### Post by Pjotr123 on 2009-11-23
Update 17 for JRE6 has (finally!) arrived in the "proposed" respository of 8.04 LTS:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/477812/comments/7](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/477812/comments/7)

Overview:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/477812](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/477812)

I've already tried the update and it works fine. It'll probably be moved to the normal update repository very soon.

Users of all other versions of Ubuntu, including 9.10, won't get this security update for JRE. They can use this how-to for manual installation:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by knottshawk on 2009-12-14
The instructions work great... however, I have a java based VPN setup that I need to use and it's not working with my 64 bit setup. Sun's website, in the Java download section, states 
> * Please use the 32-bit version for Java applet and Java Web Start support. 

Is there a way to make the 32 bit version of Java work with 64 bit Karmic?

---

### Post by francoriv on 2010-01-17
Thank you so much pjotr You are my new ubuntu yoda I've been trying to play the new version of freecol but was having trouble with my java. after 5 days and many google searches I found this,,Thank you so much for sharing your knowledge and not being a tool when people are lost and dont know what to do.. Kudo's

---

### Post by BigCityCat on 2010-01-17
OKay, I'm using Kubuntu 9.10 64bit and this worked flawlessly. Thank you very much. 

I was worried cause I finally had java working and I didn't want to screw up what I had. In the interest of security I gave it a whirl.

Once again, thank you.

---

### Post by sepius on 2010-02-28
Just got to say my thanks.

I always need to use the Sun plugin as I use Webmin extensively for my server management and use the Webmin file manager and Webmin VNC plugin which both need Sun Java, I have never had them running on iced tea.

Thanks again.

---

### Post by ENigma885 on 2010-04-02
I just want to add some notes

**1 -** In ***Install the Firefox plugin*** section, it's not clear, for a normal user, that *.mozilla* folder is present in the home directory. Because the chances are that the user will use the same terminal window which refers to */opt/java/32* as the last folder used. So, you can add
```
cd /home/USERNAME
```
before this section.

**2 -** The moved .bin file is still present in */opt/java/32 *though it has no use after installation is complete. So, you can add something like
```
sudo rm jre-6u19-linux-i586.bin
```
after the last step in installation. (update 19 is used)

**3 -** It's a question indeed; is there any way to automate this process of updating the closed-source Java? and does making a PPA for it infringe Sun's, or now it's Oracle's :D, copyrights? if not, y isn't there one?

---

### Post by Pjotr123 on 2010-04-02
> **ENigma885 said:**
> 
**3 -** It's a question indeed; is there any way to automate this process of updating the closed-source Java? and does making a PPA for it infringe Sun's, or now it's Oracle's :D, copyrights? if not, y isn't there one?

You can offer the MOTU's to help witch packaging, which is even better than a PPA....

As to your other remarks: thanks, but I want to keep the instruction as short as possible. It's already long enough. :)

By the way: I've created a new topic for update 19:
[http://ubuntuforums.org/showthread.php?t=1445413](http://ubuntuforums.org/showthread.php?t=1445413)

---

### Post by ENigma885 on 2010-04-02
> **Pjotr123 said:**
> You can offer the MOTU's to help witch packaging
I'm not sure if I got what u mean. 

> **Pjotr123 said:**
> [COLOR="Red"]Oracle[/COLOR] (Sun) has issued ...
It's better to stick to the old "**Sun Java**" as a term just not to confuse users. Btw, Sun is still a company in essence(and still owns Java). But now that company, as a whole, is owned and controlled by a larger one; which is Oracle. More correctly it's a subsidiary of Oracle. 
All in all, we have nothing to do with that :D. It's still Sun's Java.

---

