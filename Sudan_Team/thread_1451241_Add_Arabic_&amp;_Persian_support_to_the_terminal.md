---
title: "Add Arabic &amp; Persian support to the terminal"
date: 2010-04-10
forum: Sudan Team
---

### Post by zero-n on 2010-04-10
Terminal by default don't support Arabic well so we need to do some modification to allow it to work properly:

1- Install the following packages:
 ```
sudo apt-get install libfribidi0 libfribidi-dev
```2- Download & install [[COLOR=Red]**THIS**[/COLOR]]("https://launchpad.net/%7Ebehnam/+archive/ppa/+build/574785/+files/bicon_0.2.0-1ubuntu0%7Eppa4_i386.deb") package.

3- Open[COLOR=Red]** /usr/share/applications/gnome-terminal.desktop**[COLOR=Black] by any editor you like:
```
gksudo gedit /usr/share/applications/gnome-terminal.desktop
```4- Add the following line to the end of file:
```
Terminal=true
Exec=/usr/bin/bicon.bin

```5- If you have a terminal icon in desktop remove and make a new one.

6- That's all.

Now you can work well with Arabic & Persian in the terminal. You can create files, folders in both languages in a proper manner & you can can see file & folders names correctly.

Finally:
This also added Arabic & Persian support to xterm & PuTTY. 
[/COLOR][/COLOR]

---

### Post by ejlal on 2010-04-12
salam,

thank you zero-n, great job:)!

---

### Post by yasir.elsharif on 2010-04-25
Thanks zero-n, This is magnificent, fabulous, 3ageeeb .... you are the one=D>=D>=D>
 
only missing the amd-64 bit 
which is:
[https://launchpad.net/~behnam/+archive/ppa/+build/574789/+files/bicon_0.2.0-1ubuntu0~ppa4_amd64.deb]("https://launchpad.net/%7Ebehnam/+archive/ppa/+build/574789/+files/bicon_0.2.0-1ubuntu0%7Eppa4_amd64.deb")
this goes instead of step 2 where you download and install bicon package

---

### Post by zero-n on 2010-04-26
thanks for adding the link of amd-64-bit package.

---

### Post by q8istud on 2010-10-17
hello zero-n,

I'm followed your steps but still can't see any Arabic or [COLOR=Red][COLOR=Black]Persian fonts in terminal.

is your solution worked with Ubuntu 10.10 ??

thanks
[/COLOR][/COLOR]

---

### Post by zero-n on 2010-10-18
Hello [q8istud]("http://ubuntuforums.org/member.php?u=1011092"),

I am using 10.04 LTS but i have 10.10 CD i will this guide there & give you a feed back

---

### Post by LOLSKAT0R on 2010-12-06
hohooh! super thanks bro! I was just going to install [mlterm]("http://mlterm.sourceforge.net/") before I landed on your thread. Working like a charm!
Cheers!

---

### Post by koba101 on 2010-12-21
will this support RTL and connect the characters? 'cause i tried that and it doesn't do it, or is there anything i'm missing

p.s. if it does...good work

---

### Post by GNULinuxUser on 2011-01-08
[SIZE=3]I have followed your instructions and Arabic text worked fine until I noticed that my console started doing this[/SIZE]

[IMG]http://www.about-gnulinux.com/blog/wp-content/uploads/ArabConsoleBug.png[/IMG]

[SIZE=3]As you can notice, when the string grows longer of your input on the terminal it starts with a carriage return on the same line rather than prompting for your input on the next one!

Any idea of the cause? Any missing "new line" command here or there?
Thank you again. [/SIZE]

---

### Post by zero-n on 2011-01-09
Hi [GNULinuxUser]("http://ubuntuforums.org/member.php?u=1220587"),

i've faced this problem before but honestly i didn't try to solve it.

i you find out a soultion share it with me ;)

---

### Post by GNULinuxUser on 2011-01-09
> **zero-n said:**
> Hi [GNULinuxUser]("http://ubuntuforums.org/member.php?u=1220587"),

i've faced this problem before but honestly i didn't try to solve it.

i you find out a soultion share it with me ;)
I definitely will brief you with any new updates on the topic as soon as I thoroughly look into it when I get some time.
Thank you so much for your reply.

---

### Post by GNULinuxUser on 2011-01-10
I am yet interested to know if you pursued using your command line with these new modifications? 
Because I find it not convenient at all for my use!

Or did you simply uninstall the packages and it worked back again in its original setting ?

---

### Post by zero-n on 2011-01-11
no i have done Ubuntu 10.10 fresh installation on that computer to try the new Ubuntu release.

---

### Post by tx99h4 on 2012-03-15
Thanks man! 

(but if I type CTRL-ALT-T in gnome-> letters are separated, or CTRL-ALT-F1 and login it does not work --> squares appears!)

---

### Post by lancioni on 2012-05-16
Thank you for your wonderful work!

I found a minor problem with a java application using jline as an input console. When you press a backspace (independently from which keyboard you are using, Arabic or otherwise) a division by zero error occurs:

Exception in thread "main" java.lang.ArithmeticException: / by zero
    at jline.ConsoleReader.backspace(ConsoleReader.java:1414)
    at jline.ConsoleReader.backspace(ConsoleReader.java:1436)
    at jline.ConsoleReader.readLine(ConsoleReader.java:628)
    at jline.ConsoleReader.readLine(ConsoleReader.java:457)termi
    at opennlp.ccg.util.JLineReader.readLine(JLineReader.java:80)
    at opennlp.ccg.TextCCG.main(TextCCG.java:174)

In normal terminal usages, this does not happen. Nor it happen with jline if you comment out the two lines added in the terminal configuration file in order to enable bicon support.

Thank you,

Giuliano

---

### Post by BenginM on 2012-05-30
Salutation Akhy , Nice work and i salute you. :)

# but i must conform this did not work for me.

I use irssi on a screen session in gnome-termianl , the characters is set to UTF-8 i have tried severel fonst incloding GNU Unifont , makes no differance , still the Arabic letters are shown as left-aligned  .  left-to-right

# [https://bugs.launchpad.net/ubuntu/+source/vte/+bug/263822](https://bugs.launchpad.net/ubuntu/+source/vte/+bug/263822)

Salutation .

---

### Post by BenginM on 2012-06-01
> **Sary.sa said:**
> Salutation Akhy , Nice work and i salute you. :)

# but i must conform this did not work for me.

I use irssi on a screen session in gnome-termianl , the characters is set to UTF-8 i have tried severel fonst incloding GNU Unifont , makes no differance , still the Arabic letters are shown as left-aligned  .  left-to-right

# [https://bugs.launchpad.net/ubuntu/+source/vte/+bug/263822](https://bugs.launchpad.net/ubuntu/+source/vte/+bug/263822)

Salutation .

Works fine in Kconsole .

---

