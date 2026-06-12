---
title: "HOWTO: CJK in Wine (Chinese, Japanese &amp; Korean)"
date: 2007-03-13
forum: Tutorials
---

### Post by D-- on 2007-03-13
[B][COLOR="DarkRed"]The system I tested it on was 32-bit Ubuntu Feisty 7.04.

The guide is provided at users' own risk. I will try to provide support and answer questions in the thread, but if you somehow type something wrong and send your OS spiraling into /dev/null, don't blame me.[/COLOR][/B]

**[COLOR="Blue"]UPDATE: The new WineLocale 0.41 attached to this thread also supports Arabic, Greek, Hebrew and Russian. It is no longer CJK only. However, because this thread is marked CJK in Wine, I won't add the directions to it. Download the file and follow the extra steps in INSTALL to get these languages working.[/COLOR]**

OK, the web proved totally unhelpful for me to figure this out, so I imagine some of your out there in Ubuntu user-land are having the same problems.

Ordinarily, running a CJK application in Wine results in lots of garbled text. On a good day, you will get empty boxes. On a bad day, it looks like the ASCII table exploded.

No more. I put together a little shell script called WineLocale (after Microsoft's AppLocale which solves the same problem on Windows). So far, it only supports Japanese, Korean, Simplified Chinese and Traditional Chinese. I don't know enough about Hebrew, Arabic and Russian to add those. If you want to help out, by all means. Read ~/.wineloc/patches/HOWTO after installing.

The below directions are all in WineLocale's INSTALL file, but I've repeated them here because they have great generic use for anyone wondering about locales.

Just a note, purgelocales is not a solution because it refuses to show non-ASCII compatible mappings (for example, SJIS, which all pre-XP Japanese applications are).

**Step 1: Getting the Locales**

Execute the following:
```
$ cd /var/lib/locales/supported.d/
# touch ja
# touch ko
# touch zh
```

Now open up the three files in a text editor and make certain each contains the following lines.

/var/lib/locales/supported.d/ja
```
ja_JP.UTF-8 UTF-8
ja_JP SJIS
ja_JP.EUC-JP EUC-JP
```

/var/lib/locales/supported.d/ko
```
ko_KR.UTF-8 UTF-8
ko_KR.EUC-KR EUC-KR
```

/var/lib/locales/supported.d/zh
```
zh_CN.UTF-8 UTF-8
zh_TW.UTF-8 UTF-8
zh_CN GB2312
zh_CN.GBK GBK
zh_CN.GB18030 GB18030
zh_TW Big5
```

If the lines are there and everything is saved, run:

```
# dpkg-reconfigure locales
```

It will throw a warning about SJIS, but trust me, it's OK. Run the command again and everything will say "up-to-date" this time.

Next, prepare for a hellishly long download depending on which fonts you have installed (and if you live in, say, China, like me--our Ubuntu mirror sucks)

```
# apt-get install ttf-arphic-ukai ttf-arphic-uming ttf-kochi-gothic ttf-kochi-mincho ttf-mikachan ttf-mona ttf-sazanami-gothic ttf-saxanami-mincho ttf-vlgothic ttf-alee ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-unfonts ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai ttf-arphic-uming
```

Next up, even with all those installed, we will be missing a true Chinese font that handles multiple encodings. Don't suggest any of the AR fonts. It will FAIL on the menu bar of a Wine application. This step is necessary.

We will install Vera Sans YuanTi provided by the Chinese Ubuntu project. Sadly, there's no easy package for this one. We have to do:

```
$ wget http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz
$ tar -zxpvf VeraSansYuanTi.tar.gz
# mv VeraSansYuanTi /usr/share/fonts/
# fc-cache -f
# cp /etc/fonts/fonts.conf /etc/fonts/fonts.conf.old
# cp /usr/share/fonts/VeraSansYuanTi/fonts.conf /etc/fonts/
```

If you check the INSTALL file of WineLocale, you'll find information about installing Windows fonts. I will leave it out of this guide, because even without those we will get a fully functioning CJK Wine this way If you want the exact same fonts found in Window, follow that part of the guide.

**Step 2: Stealing a nice Wine setup**

The default ~/.wine/drive_c created when you run Wine sucks. Hard. It would take a lot of configuring to get something usable, so instead of suffering that, we'll steal one.

Your best bet is to get one from the IEs4Linux project. They provide an amazing setup that, when complete, will contain most of the major system DLLs. I find many applications Wine cannot normally run work fine when I use the IEs4Linux setup. So that's what this guide recommends you do.

Make sure your apt-get sources.list has universe and multiverse enabled, then run the following:

```
# apt-get update
# apt-get install cabextract wine
$ wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
$ tar zxpvf ies4linux-latest.tar.gz
$ cd ies4linux-*
$ ./ies4linux
```

Run the new "ie6" command once and close it. Now do:

```
$ rm -rf ~/.wine/*
$ cp -r ~/.ies4linux/ie6/* ~/.wine/
```

**Step 3: Install WineLocale**

Download WineLocale from my website <http://www.cinnamonpirate.com/software/winelocale/> or grab it with wget:

```
$ wget http://www.cinnamonpirate.com/pub/software/sh/wineloc-0.41.tar.gz
$ tar zxpvf wineloc-0.41.tar.gz
$ cd wineloc-0.41
$ ./install
```

This will install the WineLocale default files in /usr/local/share/wineloc and create a symlink in /usr/local/bin. You can now run "wineloc" from anywhere on your system.

**Step 4: Using WineLocale**

WineLocale, at base, is extremely easy to use. The simplest command line is:

```
$ wineloc -l zh_CN /path/to/executable.exe
```

-l is the locale flag. If omitted, WineLocale will run it in your current system locale. Valid options are:

[*]ja_JP - Japanese
[*]ko_KR - Korean
[*]zh_CN - Chinese (Simplified)
[*]zh_TW - Chinese (Traditional)

zh_HK and zh_SG will just alias to the other two Chinese modes if you use them. There is also a -o flag that will let you enable DLL overrides (use real DLLs instead of Wine's). This option is tied to a IEs4Linux created Wine setup. If you didn't use theirs, don't touch it or evil magic may happen. Hey, don't complain about "choice": you have the choice not to follow this guide :)

There's also one more option, -f, which lets you specify a different font group. "common" is the default, but there is also a "win" packed in if you followed the guide to install Windows fonts.

You can create your own font themes and overrides if you explore ~/.wineloc/patches, but that's a topic for another guide.

If you followed everything so far, congratulation, you can now run CJK applications in Wine. On launch, the registry will be hacked up to fit your locale. On exit, everything reverts back to the default so your normal Wine applications won't exhibit any odd behavior. If you manage to "crash" it so settings get stuck, you can run this command to reset all font preferences. Ignore any "errors":

```
$ regedit /usr/local/share/wineloc/patches/default.reg
```

If you check my website, you can see pictures of CJK applications running using WineLocale. To get your Wine applications looking close to the rest of your UI, you need to use "winecfg". Check section iii of INSTALL, "Configuring Wine with winecfg," to see how to do this.

Have fun :)

---

### Post by Jeremy Jackins on 2007-04-09
thank you!
this post has been so helpful, I have spent countless hours of googling trying to get japanese fonts to display in wine, without so much as a hint of progress until I found this guide.

---

### Post by D-- on 2007-04-10
No problem. Glad to hear it helped.

Trust me, I did the same. When Google proved to be absolutely no help, I realized no one had ever done this before and decided to work it out myself ;)

Everything works good I trust? I'm glad to hear one other user has tested my guide and confirmed it works.

---

### Post by Jeremy Jackins on 2007-04-13
there were one or two buttons in the installation I was running that didn't display correctly, but aside from that everything has worked perfectly so far.

---

### Post by D-- on 2007-04-13
Hi, what installer?

Generally this would be caused if they manually specified a font which is getting mapped to one on your system (for example, if you installed the win32 fonts package). You can solve this by editing one of the .reg files for your locale, adding that font, and mapping it to one with the correct locale.

The one fall-through in this is rally that hard-mapping of fonts. Say, for example, they use Arial. Well, on Japanese Windows, maybe it will shove in the missing characters from one of the Japanese fonts. However, on Wine, you don't have this link. You have to totally swap Arial with one that will have the glyphs you need. It's kind of a bummer, but that's just how it works.

---

### Post by seshomaru samma on 2007-04-13
> Next, prepare for a hellishly long download depending on which fonts you have installed (and if you live in, say, China, like me--our Ubuntu mirror sucks)

dont want to hijack the thread or anything but these mirrors are quite fast:
```
deb http://ubuntu.cn99.com/ubuntu/ dapper main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ dapper-updates main restricted universe multi verse
deb http://ubuntu.cn99.com/ubuntu/ dapper-security main restricted universe mult iverse
deb http://ubuntu.cn99.com/ubuntu/ dapper-backports main restricted universe mul tiverse
deb http://ubuntu.cn99.com/ubuntu-cn/ dapper main restricted universe multivers
```

---

### Post by Jeremy Jackins on 2007-04-14
it was the installer for Kanon, one of those visual novel dealies. it wasn't much of a problem at all, I just got <<<<<<< for text on a couple of accept/cancel buttons. this hasn't shown up anywhere else so I'm not going to worry about it =/

on a side note, borrowing a wine setup from Es4Linux is a really nice trick that has helped me out in a few cases now. I wonder why wine doesn't include more DLLs like that on their default install? legal issues I guess.

---

### Post by D-- on 2007-04-14
Out of curiosity, was it with the Linux font setup or Windows font setup?

---

### Post by D-- on 2007-04-16
**URGENT:** If you are running Feisty, DO NOT INSTALL UPDATES RIGHT NOW. A new round of updates that rolled out in the last 24 hours has smashed locale support. You cannot install SJIS, GB2312 or GB18030 anymore. This means WineLoc will fail at running Japanese and Simplified Chinese software. At the moment, only Korean and Traditional Chinese are still working.

I've posted about it in [this thread](http://ubuntuforums.org/showthread.php?p=2460587). Hopefully someone comes up with an answer, or a new round up updates is quickly released to fix the problem.

**EDIT:** I've worked out a fix. If you update and these locales suddenly quit working, open the Ubuntu Language Support tool and uncheck Japanese and Chinese. Click apply, then close. Repeat the directions in my INSTALL file to add the locales again to /var/lib/locales/supported.d/, run a `dpkg-reconfigure locales` and log out of gdm. When you log back in, everything will work fine again.

---

### Post by Jeremy Jackins on 2007-04-22
> **D-- said:**
> Out of curiosity, was it with the Linux font setup or Windows font setup?
I'm not 100% sure, I didn't specify the -f option if that's what you mean so I suppose I was using the linux font setup.

---

### Post by D-- on 2007-04-24
Double-check that you don't have Tahoma installed. There's some places in the Wine config I didn't override Tahoma, so if you have that installed, it attempts to use Tahoma instead, which means all this language support stuff breaks.

---

### Post by Chris Kerr on 2007-04-30
I am running Ubuntu 7.04 with Japanese locales and am trying to get two windows dictionary applications, Jamming and DDwin to work under wine. I have no problem with the display of Japanese characters but I cannot input Japanese characters - A small Wine IME opens and allows Japanese character input but when the characters are input into the application they appear as question marks etc.&#12288;Do you know how to get Japanese input working under wine?

---

### Post by D-- on 2007-05-01
That I can't help with. I have to use IE for some of my banking stuff that runs on ActiveX and need to be able to enter Chinese. Have not found ANY way to pull it off. I currently type in Mousepad in X and just copy and paste it into the Windows application.

If you come up with a better solution, please share.

---

### Post by Chris Kerr on 2007-05-02
Thanks for your reply. I guess a similar copy and paste technique to enter Japanese into the applications I want to use. 

On another note, after following your instructions for  "CJK in wine" I found that Japanese characters are garbled on man pages displayed in the Ubuntu Help Center, but are not displayed correctly within a terminal window. On my other ubuntu machine Japanese characters are displayed correctly in the Ubuntu Help Center. 

I tried restoring my locales to what they were previously but I still get garbled Japanese characters for man pages in the Ubuntu Help Center.

Heres what my system looks like now:

chris@vaio:~$ more /var/lib/locales/supported.d/ja
ja_JP.UTF-8 UTF-8

chris@vaio:~$ locale -a
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ja_JP.utf8

Do you know how I can get my man pages to be correctly displayed in Ubuntu help center again?

---

### Post by D-- on 2007-05-15
Try an:```
$ echo $LANG
```It sounds like this may be a problem of your machine locale being in SJIS.

---

### Post by donpoon on 2007-05-19
I've been having problem setting up my CJK wine.

I couldn't finish downloading VeraSansYuanTi.tar.gz.  "download.ubuntu.org.cn" is always slow to me and the connection close and the download abort.  I have download the VeraSansYuanTi from an alternative source and it's in zip instead.  I skipped installing that part and go through the rest of the setup.

When I start running a Big5 program using "wineloc -l zh_TW /path/to/executable.exe", It shows some interface in Big5 but it shows lots of things in Korean.  Wonder if you know where did I make a mistake...

---

### Post by donpoon on 2007-05-20
VeraSansYuanTi fonts is critical (as mentioned in the original guide).  I use wget unlimited retries (more than 150 retrys) to download the fonts eventually.  After setting up the VeraSansYuanTi fonts, everything works fine.  Now I have a convenient CJK Wine environment.  No more existing X Windows and choosing other Languages.

Thank you so much for this great tool!

---

### Post by D-- on 2007-05-28
I'll try to track down another mirror for the font that will be easier for people outside China. I live here, so it was super quick for me.

---

### Post by IFailAtLinux on 2007-05-28
I just tried doing that but apt-get couldn't find ttf-saxanami-mincho package... I went on anyway and now while running 'wineloc -l ja_JP application' I don't get japanese fonts anyway, I probably did something wrong...

But now setup.exe for one program works even worse than it did before, because I get 'Error writing to the temporary location' while trying to start it with both wine and wineloc(before I would get to at least click next 2 times).

---

### Post by D-- on 2007-05-29
IFailAtLinux: To be honest, most of those fonts aren't even needed. I just make you install them so users inclined to tweak their settings have some fonts to pick from. VeraSansYuanTi is the important one. If you don't install it, then it probably will not work. Unfortunatly, no Ubuntu sites have seen fit to mirror the official Chinese Ubuntu site, so that is the only place to get it.

As for your error. This sounds like a corrupt Wine installation.

Did you follow my instructions which say to use IEs4Linux as a base? If not, whack yourself on the head for failing at Linux. HOWTOs only work when you follow all the directions. If you did follow my directions, then do the following:

```
$ rm -rf ~/.wine/
$ mkdir ~/.wine
$ cp -r ~/.ies4linux/ie6/* ~/.wine/
```

You should be all set again.

Also, check to make sure /tmp is not on a full-up partition. If Wine is mapping temp files there (possibly symlinking ~/.wine/drive_c/windows/temp?) that could cause an error.

---

### Post by IFailAtLinux on 2007-06-03
Well, those 3 lines did help(I followed your tutorial step by step, only thing changed was not installing the one font mentioned before). My ubuntu mirrors seem to be quite good as everything was downloading with max speed :3

Anyway, those 3 lines unborked things, but applications still don't show Japanese fonts under wine. When trying:

wineloc -l ja_JP app.exe //tried few of them

I get this output in console. I don't know much about linux, but for me everything seems to be doing just fine... (I closed this application as soon as I confirmed it had '???' instead of what should be there)

```

WineLocale 0.3 - CJK Launcher for Wine (cli)
Using locale file /usr/local/share/wineloc/patches/common/ja_JP.reg ...
Setting up Japanese Shift-JIS locale ...
Executing application ...
Restoring old Wine locale settings

```

Sorry I haven't answered anything for last few days, I was really busy with work.

Edit:>

Oh, I just realized something~
Your method can give people some nasty errors, which can easily be fixed.

```

Fontconfig warning: no <cachedir> elements found. Check configuration.
Fontconfig warning: adding <cachedir>/var/cache/fontconfig</cachedir>
Fontconfig warning: adding <cachedir>~/.fontconfig</cachedir>

```

Why does it happen?
When you do this step:
```

# cp /usr/share/fonts/VeraSansYuanTi/fonts.conf /etc/fonts/

```
fonts.conf copied _might_ lack information about cachedir, so obviously it'll cause problems in such case.

Fix is easy:
Add following lines to new fonts.conf: (they might differ for you, so check them at font.conf.old, created step earlier and copy them to fonts.conf).

```

<!-- Font cache directory list -->

	<cachedir>/var/cache/fontconfig</cachedir>
	<cachedir>~/.fontconfig</cachedir>

```

---

### Post by D-- on 2007-06-06
Can you provide me with any of these EXEs? All the Japanese software I tested works great, but I cannot do any further debugging without the files to test.

---

### Post by IFailAtLinux on 2007-06-09
Sure, here is the link for the download of app called metasequoia. It's 5mb big so it shouldn't be much of bandwitch problem. It has an option to run in either english or japanese, and japanese comes up as nothing but gibberish for me.

I hope it will work for you, that would mean I just did something wrong and that it's fixable :3

---

### Post by D-- on 2007-06-09
You forgot the link.

---

### Post by IFailAtLinux on 2007-06-10
Ah, lol. I'm pretty amazed at myself right now.

The download page:
[http://www.metaseq.net/metaseq/download.htm](http://www.metaseq.net/metaseq/download.htm)
Get metaseq242.zip

---

### Post by D-- on 2007-06-23
It runs perfectly for me. Did you remember to install the Vera Sans YuanTi font? That is a REQUIRED step.

```
d@cinnamon:~/Desktop/meta$ wineloc -l ja_JP Metaseq.exe
WineLocale 0.4 - CJK Launcher for Wine (cli)
ja_JP
Using locale file /usr/local/share/wineloc/patches/common/ja_JP.reg ...
Setting up Japanese Shift-JIS locale ...
Executing application ...
fixme:time:GetCalendarInfoW Unimplemented caltype 4
fixme:time:GetCalendarInfoW Unimplemented caltype 3
fixme:win:WINNLSEnableIME hUnknown1 0x1006c bUnknown2 0: stub!
fixme:win:WINNLSEnableIME hUnknown1 0x1006c bUnknown2 -1: stub!
fixme:win:WINNLSEnableIME hUnknown1 0x10072 bUnknown2 0: stub!
fixme:win:WINNLSEnableIME hUnknown1 0x10072 bUnknown2 -1: stub!
fixme:win:WINNLSEnableIME hUnknown1 0x1006c bUnknown2 0: stub!
fixme:win:WINNLSEnableIME hUnknown1 0x1006c bUnknown2 -1: stub!
```

Edit: I just noticed from your code snippet that you are using version 0.3. As you can see, I am using 0.4. That is the attachment currently int he first post of this thread. I suggest you update and try it again. I honestly can't recall changing anything that would fix this in 0.4, but who knows.

---

### Post by leeyee on 2007-06-23
Aha, i am from Nanjing, that's great to see Chinese here, and really great tutorial. Thanks for your nice work.

---

### Post by D-- on 2007-06-24
> **leeyee said:**
> Aha, i am from Nanjing, that's great to see Chinese here, and really great tutorial. Thanks for your nice work.

Actually, I'm not Chinese. I just moved here a few years ago. Far better than where I used to live ...

---

### Post by IFailAtLinux on 2007-06-24
Actually I changed my default system language to polish and now wine got completely messed up. Some apps that did work before are broken now, while Japanese locale works wonderfully... I didn't change anything else on my system so nothing else can be the problem.

---

### Post by D-- on 2007-06-24
Sorry. I can't offer an explanation. This method has worked great for me and others, and I tested it fully on a default English Ubuntu installation.

---

### Post by IFailAtLinux on 2007-06-24
Well, I'll try playing around with that, now that I know what might be breaking it I'm determined to find a solution... In free time.

---

### Post by D-- on 2007-07-02
> **IFailAtLinux said:**
> Well, I'll try playing around with that, now that I know what might be breaking it I'm determined to find a solution... In free time.

I found it!

I did a fresh Fesity install this weekend. It seems some old locale mappings are deprecated. I found some of my Chinese lines broke, and when I tested out Japanese, it was broke too.

This should fix it for you. Head back to page 1 and download the new 0.41 release. ;)

---

### Post by Kanji_Man on 2007-07-06
> **D-- said:**
> Next, prepare for a hellishly long download depending on which fonts you have installed (and if you live in, say, China, like me--our Ubuntu mirror sucks)

```
# apt-get install ttf-arphic-ukai ttf-arphic-uming ttf-kochi-gothic ttf-kochi-mincho ttf-mikachan ttf-mona ttf-sazanami-gothic ttf-saxanami-mincho ttf-vlgothic ttf-alee ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-unfonts ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai ttf-arphic-uming
```

First off I want to thank you for this tutorial, I use it often and is more useful than any other CJK/Wine resource I can find.  However, I believe there is a type-o in this instruction. I may be mistaken but I believe the font "ttf-saxanami-mincho" should be "ttf-sazanami-mincho". Also, most of these commands require the user to either use fakeroot or sudo. It would also be a lot easier to copy/paste your commands if you did not begin them with a character for the prompt.

```
sudo apt-get install ttf-arphic-ukai ttf-arphic-uming ttf-kochi-gothic ttf-kochi-mincho ttf-mikachan ttf-mona ttf-sazanami-gothic ttf-sazanami-mincho ttf-vlgothic ttf-alee ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-unfonts ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai ttf-arphic-uming
```

Now that you have begun to expand wineloc to include more languages, have you considered contacting the wine development team to see if they can use your strategy to possibly implement locales into winecfg?

One more thing, it appears ubuntu china may no longer be offering VeraSansYuanTi.tar.gz, is there an alternative source for this font? I am receiving 404 Not Found errors when trying to download the file, and I know it used to work.

---

### Post by tripmix on 2007-07-16
Anyone tried this in debian? We dont have the /var/lib/locales/supported.d/ dir. Do you think I could just skip the first steps and go right to "dpkg-reconfigure locales"?

Hmm... Why am I typing this?? It's not like I'm gonna wait for an answer before I try...

---

### Post by D-- on 2007-07-16
Hi, no idea about Debian.

Kanji_Man: Thanks for your info. I will get that fixed pronto. I have a GUI version int he works via PHP-GTK. It works exactly like AppLocale for Windows, and the response I've gotten has been pretty positive. If someone wants to rewrite it in another language, that's their business, but I only know PHP-GTK.

I use the console marks #/$ because that is standard in most guides on this site. It tells a user whether the command needs to be executed as root or not. I would never advise executing any command as root that does not specifically need to be.

I would love to repost Vera Sans YuanTi, but I cannot afford to host a 70MB high traffic file on my webspace. I've put it on RapidShare at ([http://rapidshare.com/files/43354195/VeraSansYuanTi.7z.html](http://rapidshare.com/files/43354195/VeraSansYuanTi.7z.html)), but it would be nice to have it hosted somewhere more ... stable.

---

### Post by petercool on 2007-08-22
This is what i saw when i typed the command:wineloc -l zh_TW /path/to/executable.exe

WineLocale 0.41 - CJK Launcher for Wine (cli)
Error: Specified file '/path/to/executable.exe' not found

Could you give me an easier example for dummies:popcorn:
thx a million

---

### Post by petercool on 2007-08-22
thx.............the problem solved:lolflag:

> **petercool said:**
> This is what i saw when i typed the command:wineloc -l zh_TW /path/to/executable.exe

WineLocale 0.41 - CJK Launcher for Wine (cli)
Error: Specified file '/path/to/executable.exe' not found

Could you give me an easier example for dummies:popcorn:
thx a million

---

### Post by Kanji_Man on 2007-10-27
> **D-- said:**
> ```
$ wget http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz
$ tar -zxpvf VeraSansYuanTi.tar.gz
# mv VeraSansYuanTi /usr/share/fonts/
# fc-cache -f
# cp /etc/fonts/fonts.conf /etc/fonts/fonts.conf.old
# cp /usr/share/fonts/VeraSansYuanTi/fonts.conf /etc/fonts/
```
I was setting up another system today and was reminded of a problem I have been running accross and it took me a bit to trace down the problem. The fonts.conf included int he VeraSansYuanTi package which gets replaced in the section above does not contain entries for the fontconfig cacche directories. This eventually causes fontconfig to start complaining about it. To resolve this issue I simply copied the cachedir headers out of the old fonts.conf and added them to the new one::
```
sudo gedit /etc/fonts/fonts.conf
```
Locate this section:
```
-->

   <dir>/usr/share/fonts</dir>
   <dir>/usr/X11R6/lib/X11/fonts/Type1</dir> <dir>/usr/local/share/fonts</dir>
   <dir>~/.fonts</dir>

<!--
```
And change it to look like this:
```
-->

   <dir>/usr/share/fonts</dir>
   <dir>/usr/X11R6/lib/X11/fonts/Type1</dir> <dir>/usr/local/share/fonts</dir>
   <dir>~/.fonts</dir>

<!-- Font cache directory list -->

	<cachedir>/var/cache/fontconfig</cachedir>
	<cachedir>~/.fontconfig</cachedir>

<!--
```

I'd also like to point out that the ttf-sazanami-mincho font is still listed as ttf-saxanami-mincho in your instructions (x should be a z).

Thank you again for this tutorial and your hard work creating winelocale. I use these instructions often and they continue to be the best reference on the net for setting up multilingual wine and I am happy to report that this approach still works well with Gutsy.

---

### Post by sutem on 2007-11-14
the true type chinese fond verasansyuanti can't be downloaded from link above 

try this out.

wget [http://download.linuxsir.org/FreeTTF/VerAsanSyuanti/verasansyuanti.tar.bz2](http://download.linuxsir.org/FreeTTF/VerAsanSyuanti/verasansyuanti.tar.bz2)

---

### Post by daengbo on 2007-12-03
I want to thank you. I spent too many hours trying to figure out how to run my school's required CoolMessenger (a Korean piece of software). wineloc finally did it! Great love to you!

---

### Post by D-- on 2007-12-26
Hi everyone. Great news. I've been working more on WineLoc an have a graphical+cli version almost ready using PHP-GTK. I also have created install script to handle all the ugly configuration settings from the first part of this thread automatically.

It also no longer depends on VeraSansYuanTi to work.

Starting early next year, it will be possible to install WineLoc entirely from apt/synaptic with no configuration needed. :)

---

### Post by umarsaid on 2008-01-10
The VeraSansYuanTi.tar.gz is not available anymore at [http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz](http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz) and [http://download.linuxsir.org/FreeTTF/VerAsanSyuanti/verasansyuanti.tar.bz2](http://download.linuxsir.org/FreeTTF/VerAsanSyuanti/verasansyuanti.tar.bz2) always timeout. Can you provide working link or attach one to umarsaid in gmail.com?

TIA

> **tripmix said:**
> Anyone tried this in debian? We dont have the /var/lib/locales/supported.d/ dir. Do you think I could just skip the first steps and go right to "dpkg-reconfigure locales"?


All locales is put in /etc/locale.gen

---

### Post by umarsaid on 2008-01-10
> **umarsaid said:**
> The VeraSansYuanTi.tar.gz is not available anymore at [http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz](http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz) and [http://download.linuxsir.org/FreeTTF/VerAsanSyuanti/verasansyuanti.tar.bz2](http://download.linuxsir.org/FreeTTF/VerAsanSyuanti/verasansyuanti.tar.bz2) always timeout. Can you provide working link or attach one to umarsaid in gmail.com?

TIA


I'm sorry for not reading previous posts carefully. It has been uploaded to RapidShare. But if there are other hosts other than rapidshare, it will be great, since my internet connection is very slow and often disconnected.

---

### Post by pencilcheck on 2008-01-20
Thx for the hard work :)
Now you have solved one of my biggest problem in using wine to run one of my japanese games.
Hooray!!!

---

### Post by tenchu77491 on 2008-02-11
EDIT: Problem fixed so far... had to re-do everything.

---

### Post by Askrates on 2008-02-21
First of all, Massive respect to D-- for this guide. I hope some wine developers are taking note of his great work.

Now for a comment - Would it be an idea to split this tutorial up into Chinese | Korean | Japanese | whatever? Downloading 100 MB+ of fonts from a lot of different languages may be overkill, when all you need is Japanese for example.:)

---

### Post by hramrach on 2008-02-25
Hello,

Thanks for this guide. The scripts do not work perfectly for me (perhaps because I run Debian, not Ubuntu) so I do the switching manually. However, it provides the important pieces of information

a) it worked for somebody already

b) what encoding is used for various languages in Windows

Of course using this method you cannot get proper input in Wine. Perhaps for Russian or Greek which  use direct keyboard input but certainly not for CJK.

The reason is simple. All these scripts do is 

1) set up default wine fonts so that they contain the characters for the given language. As there are no quality fonts in Linux that would support multiple language groups (Latin/Greek/Cyrillic/CJK/..) it is necessary to switch the fonts each time.

2) run wine in the windows encoding corresponding to the desired language. As the text in the application is encoded in some legacy encoding and not utf-8 this is necessary for the application to display properly (unless the application uses Unicode, but few do even of the windows bundled applications - regardless of MS recommendations).

If you run wine like that you can see the text rendered properly but you cannot type. That's because your input method runs in utf-8 but wine runs in some legacy windows encoding. The text wine gets from your input method is wrong. If you modify the scripts to run another X application (like xterm) instead of wine you won't be able to type in that application either. You would have to run your whole X session in the legacy encoding for input to work.

However, there is good chance that some applications do not need step 2). As IE6 is quite new and can handle various encodings it might be already unicode. If you are running IE and have trouble writing CJK in it it might be worth trying to just import the registry settings for your language and then run wine normally.

Currently the only input problem in WIne I know of is cursor positioning. When you convert some text and send it to wine it fails to reposition the cursor. The cursor stays before the text you just typed although wine thinks it has moved after the text. If you move the cursor or type more text it will appear at the right place.

---

### Post by bc991122 on 2008-05-23
Dear all,

I tried to run Visual Foxpro under wine ,however I cannot display some data in Chinese

I have tried  "wineloc -l zh_TW XXX.prg"
I have tried  "LANG=zh_TW  wine XXX.prg"
Both cases, Traditional Chinese data cannot be displayed" while Foxpro runs

I think Foxpro is a non-unicode program, how wine deals with a non-unicode program, will changing codepage used by wine be of any help ?

Thanks for advice
Brian

---

### Post by D-- on 2008-05-25
Hey guys, I love you all a whole lot more than the Wine team does.

The project is registered on GoogleCode now, and as soon as I get a few more things taken care of in the new Python version, I will make the initial SVN merge.

I am willing to take criticism on the UI. I attempted to keep it uniform, scalable and minimal. It is coded in Python with pygtk, meaning it functions perfectly on an initial Ubuntu install without needing special packages. It is written with the same thing all Ubuntu tools are.

I have also slashed out Vera Sans YuanTi and now have things running with packaged fonts for Linux. The current overhead packages are: ttf-arphic-uming, ttf-sazanami-gothic, ttf-sazanami-mincho, ttf-baekmuk, culmus

I may explore breaking this up into different parts in future versions, such as having winelocale, then subpackages like winelocale-ja which would pull the Japanese fonts and unlock Japanese in the options menu. This would solve things for people who are worried about the download size, though I would expect these requirements are far less than users previously dealt with.

[img]http://cinnamonpirate.com/winelocale.png[/img]

Mind you I am not a professional programmer, so I don't have much experience with this kind of thing. I am just another user who is sick of watching "work in languages besides English" bumped to the end of Wine's TODO list for the last decade. My main work is in media, and with the earthquakes here in China and the upcoming Olympics, I have been kind of tied up :(

My goal is to get a Debian package out that automates all that code page crap and installs the new Python version by the middle of June.

---

### Post by benmoran on 2008-06-18
really looking forward to the GUI. Thanks!

---

### Post by nooblot on 2008-06-29
Um so is there an easier way to do this basic thing with the "latest & greatest" --- Hardy & Wine 1.1 ???

---

### Post by Ryuho on 2008-07-04
hmm I get the error:

[email]ryuho@ryuho-laptop:~/.wine[/email]$ wineloc -l ja_JP ~/Downloads/2chtubo200.exe 
WineLocale 0.41 - CJK Launcher for Wine (cli)
ja_JP
Using locale file /usr/local/share/wineloc/patches/common/ja_JP.reg ...
Setting up Japanese Shift-JIS locale ...
err:service:RPC_MainLoop RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
Executing application ...
err:service:RPC_MainLoop RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
Restoring old Wine locale settings
err:service:RPC_MainLoop RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
[email]ryuho@ryuho-laptop:~/.wine[/email]$ 


wine --version
wine-0.9.59

---

### Post by SadaraX on 2008-08-24
I hope this is not useless information, but I have been using Japanese programs in Wine for awhile now with a much simpler method:

```
LANG=ja_JP.UTF-8 wine application.exe
```

I am sure this does not work for all languages and applications, but I thought this information might be useful for some people. I have Japanese language support installed on my Linux system and some Wine MS font packs installed, though I do not think they are anything very exotic or special.

This information was indirectly mentioned by bc991122 on May 23rd, 2008.

---

### Post by modmadmike on 2008-08-30
I tried your guide but no luck :( the program is a Japanese Character learning program called "KanaLearn" The characters just appear as boxes should i just run it in a virtualbox?

---

### Post by Jinnai on 2008-10-23
tried the program, but unfortunately it didn't work. My error was before install process, something along the lines that "This isn't a Japanese Windows OS" or the like. This doesn't happen in XP with East-Asian Fonts enabled and the non-unicode characters set to Japanese (the language of the program), so it's it's something to do with detecting proper font setup I guess.

---

### Post by Scyron on 2008-11-10
I've applied this guide on every ubuntu install I've used since Feisty. Now I'm on Intrepid and it doesn't work. =(

It doesn't seem to accept the YuanTi fonts.conf file, for starters. I tried editing it so it uses a cachedir, but the fonts still don't display... getting errors like this

```
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703

```

---

### Post by hramrach on 2008-12-09
Hello

I tried to report the problem on Wine bugzilla ..

It turns out the right approach is not font substitution but font linking.

That way the font can have *all* characters, you do not have to switch them.

However, the inability to type in some applications is not resolved.

The font linking is poorly designed (it's MS feature after all). You have to specify the font name as well as the font filename for the linking to work.

I have some files lying around which have sample of font links so perhaps somebody finds them useful.

You can only view them by importing them into the registry as regedit dumps the values as hex when they are stored in the .reg file. Another "nice" feature.



Windows Registry Editor Version 5.00

; Windows linking

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontLink\SystemLink]
"Lucida Sans Unicode"=hex(7):4d,00,53,00,47,00,4f,00,54,00,48,00,49,00,43,00,\
  2e,00,54,00,54,00,43,00,2c,00,4d,00,53,00,20,00,55,00,49,00,20,00,47,00,6f,\
  00,74,00,68,00,69,00,63,00,00,00,00,00
"MS UI Gothic"=hex(7):53,00,69,00,6d,00,53,00,75,00,6e,00,2e,00,54,00,54,00,43,\
  00,2c,00,53,00,69,00,6d,00,53,00,75,00,6e,00,00,00,67,00,75,00,6c,00,69,00,\
  6d,00,2e,00,74,00,74,00,63,00,2c,00,67,00,75,00,6c,00,69,00,6d,00,00,00,6d,\
  00,69,00,6e,00,67,00,6c,00,69,00,75,00,2e,00,74,00,74,00,63,00,2c,00,50,00,\
  4d,00,69,00,6e,00,67,00,4c,00,69,00,55,00,00,00,00,00
"Tahoma"=hex(7):4d,00,53,00,47,00,4f,00,54,00,48,00,49,00,43,00,2e,00,54,00,54,\
  00,43,00,2c,00,4d,00,53,00,20,00,55,00,49,00,20,00,47,00,6f,00,74,00,68,00,\
  69,00,63,00,00,00,53,00,69,00,6d,00,53,00,75,00,6e,00,2e,00,54,00,54,00,43,\
  00,2c,00,53,00,69,00,6d,00,53,00,75,00,6e,00,00,00,67,00,75,00,6c,00,69,00,\
  6d,00,2e,00,74,00,74,00,63,00,2c,00,67,00,75,00,6c,00,69,00,6d,00,00,00,6d,\
  00,69,00,6e,00,67,00,6c,00,69,00,75,00,2e,00,74,00,74,00,63,00,2c,00,50,00,\
  4d,00,69,00,6e,00,67,00,4c,00,69,00,55,00,00,00,00,00
"Microsoft Sans Serif"=hex(7):4d,00,53,00,47,00,4f,00,54,00,48,00,49,00,43,00,\
  2e,00,54,00,54,00,43,00,2c,00,4d,00,53,00,20,00,55,00,49,00,20,00,47,00,6f,\
  00,74,00,68,00,69,00,63,00,00,00,53,00,69,00,6d,00,53,00,75,00,6e,00,2e,00,\
  54,00,54,00,43,00,2c,00,53,00,69,00,6d,00,53,00,75,00,6e,00,00,00,67,00,75,\
  00,6c,00,69,00,6d,00,2e,00,74,00,74,00,63,00,2c,00,67,00,75,00,6c,00,69,00,\
  6d,00,00,00,6d,00,69,00,6e,00,67,00,6c,00,69,00,75,00,2e,00,74,00,74,00,63,\
  00,2c,00,50,00,4d,00,69,00,6e,00,67,00,4c,00,69,00,55,00,00,00,00,00

REGEDIT4

; most likely some attempt at replicating the above on Wine

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontLink\SystemLink]
"Lucida Sans Unicode"=hex(7):4d,53,47,4f,54,48,49,43,2e,54,54,43,2c,4d,53,20,\
  55,49,20,47,6f,74,68,69,63,00,00
"MS UI Gothic"=hex(7):53,69,6d,53,75,6e,2e,54,54,43,2c,53,69,6d,53,75,6e,00,67,\
  75,6c,69,6d,2e,74,74,63,2c,67,75,6c,69,6d,00,6d,69,6e,67,6c,69,75,2e,74,74,\
  63,2c,50,4d,69,6e,67,4c,69,55,00,00
"Tahoma"=hex(7):4d,53,47,4f,54,48,49,43,2e,54,54,43,2c,4d,53,20,55,49,20,47,6f,\
  74,68,69,63,00,53,69,6d,53,75,6e,2e,54,54,43,2c,53,69,6d,53,75,6e,00,67,75,\
  6c,69,6d,2e,74,74,63,2c,67,75,6c,69,6d,00,6d,69,6e,67,6c,69,75,2e,74,74,63,\
  2c,50,4d,69,6e,67,4c,69,55,00,00
"Microsoft Sans Serif"=hex(7):4d,53,47,4f,54,48,49,43,2e,54,54,43,2c,4d,53,20,\
  55,49,20,47,6f,74,68,69,63,00,53,69,6d,53,75,6e,2e,54,54,43,2c,53,69,6d,53,\
  75,6e,00,67,75,6c,69,6d,2e,74,74,63,2c,67,75,6c,69,6d,00,6d,69,6e,67,6c,69,\
  75,2e,74,74,63,2c,50,4d,69,6e,67,4c,69,55,00,00

REGEDIT4

; Windows style substitutions

[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\FontSubstitutes]
"Arial CE,238"="Arial,238"
"Arial CYR,204"="Arial,204"
"Arial Greek,161"="Arial,161"
"Arial TUR,162"="Arial,162"
"Courier New CE,238"="Courier New,238"
"Courier New CYR,204"="Courier New,204"
"Courier New Greek,161"="Courier New,161"
"Courier New TUR,162"="Courier New,162"
"Helv"="MS Sans Serif"
"Helvetica"="Arial"
"MS Gothic"="IPAGothic"
"MS Mincho"="IPAMincho"
"MS PGothic"="IPAPGothic"
"MS PMincho"="IPAPMincho"
"MS Shell Dlg"="MS UI Gothic"
"MS Shell Dlg 2"="Tahoma"
"MS UI Gothic"="IPAUIGothic"
"Times"="Times New Roman"
"Times New Roman CE,238"="Times New Roman,238"
"Times New Roman CYR,204"="Times New Roman,204"
"Times New Roman Greek,161"="Times New Roman,161"
"Times New Roman TUR,162"="Times New Roman,162"
"Tms Rmn"="MS Serif"



REGEDIT4
; Wine hack

[HKEY_USERS\S-1-5-4\Software\Wine\Fonts\Replacements]
"MS UI Gothic"="IPAUIGothic"
"MS Gothic"="IPAGothic"
"MS PGothic"="IPAPGothic"
"MS Mincho"="IPAMincho"
"MS PMincho"="IPAPMincho"

---

### Post by D-- on 2009-01-10
Hey guys ...

[SIZE="6"]I'M SO HAPPY![/SIZE] :D

That's on Intrepid, for all the people who posted the old method is having problems.

hramrach is right about FontLink, but it is entirely useless without MS Fonts. Wine has essentially no support for it at this point. I have created some FontLink lines for fallback into Free fonts but it's all moot till the Wine team does their end.

So, in the mean time, some font swapping is necessary: especially for MS Shell Dlg (cannot display tab titles without swapping).

This version totally solves all locale hacking issue at the start of this thread. It carries a package payload of less than 100KB right now and works on an Ubuntu default install--no extra packages needed! Its only dependencies are a few fonts Ubuntu installs as recommended packages of ubuntu-desktop and wine (obviously).

Currently, Chinese (traditional and simplified), Japanese and Korean are working perfectly. Russian works, but I'm working to resolve a chunky font issue. Arabic and Hebrew are having problems, and I haven't tested Greek.

This release will include a toggle to flip 96/120dpi fonts in Wine. It will also read your Gtk theme to find out your font and menubar size, then hacks Wine to match for real (10pt in 96dpi X is much, much different from 10pt in Wine). It also has a toggle to enable/disable rudimentary font anti-aliasing.

It also supports localizations, as you can see from the screenshot. Currently we have English and Chinese (simplified). If you can, please help by translating [http://winelocale.googlecode.com/svn/trunk/current/i18n/en_US.lang](http://winelocale.googlecode.com/svn/trunk/current/i18n/en_US.lang) into your language. Post it here or email it to me at derrick%0cinnamonpirate%1com (/@/./ #fix the marks) and I'll add it to the SVN. Anything sent in by mid-next week should make it out in the beta. It will check the language of your Ubuntu and, assuming someone made a locale, it will show in your language. Otherwise, it defaults to English.

I still have to finish up the shortcut generation and command line mode, but I'm shooting for a beta in the next couple days. SVN has a the working implementation sans command line. I also need to get it to kill out the main core instead of hanging the WineLocale window till the Wine app exits, but that should be a trivial fix. When it's all set I'll put a downloadable .deb package on Google Code and add it to the CinnamonPirate.com Ubuntu repository.

[img]http://i153.photobucket.com/albums/s223/dsobodash/WineLocale/winelocal-061.png[/img]

---

### Post by temporary11 on 2009-01-21
thanks very much for your HOWTO

---

### Post by rexregum on 2009-02-08
Thanks for the HOW-TO.  I finally got Japanese output working.

However, I also need to be able to input Japanese.

It seems SCIM-Anthy doesn't carry over to Wine.  Nor does cutting-and-pasting work.

Any advice would be appreciated.

---

### Post by lavarock on 2009-02-12
Just want to say thank you so much for this guide, this is like the only guide about this subject on the net:-)

I will drop a line if I get PDIC(with eijiro) to work properly in wine.  It works flawless but all the fonts are garbled up.

---

### Post by BuntuFirstTimer on 2009-02-22
In front of a command, what does $ mean and what does # mean?

Update: so far I almost did the whole procedure. Though the problem is that,

```
WineLocale 0.41 - CJK Launcher for Wine (cli)
Error: Specified file '/path/to/executable.exe' not found
```

I encounter this error. Any ideas?

---

### Post by lavarock on 2009-03-04
> **BuntuFirstTimer said:**
> In front of a command, what does $ mean and what does # mean?

Update: so far I almost did the whole procedure. Though the problem is that,

```
WineLocale 0.41 - CJK Launcher for Wine (cli)
Error: Specified file '/path/to/executable.exe' not found
```

I encounter this error. Any ideas?

Don't copy the $ and #, just the command after that.
What he meant was type in whatever path your exe file is located in the place of '/path/to/executable.exe'


My problem is that I am unable to get wineloc to work with PDIC, (it runs without wineloc, but display garbled text).

---

### Post by TrueLugia121 on 2009-06-27
hi. great tutorial. e would it be possible to do the same procedure to Linux Mint 7 Gloria installed on my father's laptop?

---

### Post by michaelbr on 2009-06-28
> **D-- said:**
> Hey guys ...

[SIZE="6"]I'M SO HAPPY![/SIZE] :D

That's on Intrepid, for all the people who posted the old method is having problems.

hramrach is right about FontLink, but it is entirely useless without MS Fonts. Wine has essentially no support for it at this point. I have created some FontLink lines for fallback into Free fonts but it's all moot till the Wine team does their end.

So, in the mean time, some font swapping is necessary: especially for MS Shell Dlg (cannot display tab titles without swapping).

This version totally solves all locale hacking issue at the start of this thread. It carries a package payload of less than 100KB right now and works on an Ubuntu default install--no extra packages needed! Its only dependencies are a few fonts Ubuntu installs as recommended packages of ubuntu-desktop and wine (obviously).

Currently, Chinese (traditional and simplified), Japanese and Korean are working perfectly. Russian works, but I'm working to resolve a chunky font issue. Arabic and Hebrew are having problems, and I haven't tested Greek.

This release will include a toggle to flip 96/120dpi fonts in Wine. It will also read your Gtk theme to find out your font and menubar size, then hacks Wine to match for real (10pt in 96dpi X is much, much different from 10pt in Wine). It also has a toggle to enable/disable rudimentary font anti-aliasing.

It also supports localizations, as you can see from the screenshot. Currently we have English and Chinese (simplified). If you can, please help by translating [http://winelocale.googlecode.com/svn/trunk/current/i18n/en_US.lang](http://winelocale.googlecode.com/svn/trunk/current/i18n/en_US.lang) into your language. Post it here or email it to me at derrick%0cinnamonpirate%1com (/@/./ #fix the marks) and I'll add it to the SVN. Anything sent in by mid-next week should make it out in the beta. It will check the language of your Ubuntu and, assuming someone made a locale, it will show in your language. Otherwise, it defaults to English.

I still have to finish up the shortcut generation and command line mode, but I'm shooting for a beta in the next couple days. SVN has a the working implementation sans command line. I also need to get it to kill out the main core instead of hanging the WineLocale window till the Wine app exits, but that should be a trivial fix. When it's all set I'll put a downloadable .deb package on Google Code and add it to the CinnamonPirate.com Ubuntu repository.



First of all, I would like to thank you for this great job and for sharing it. Sorry for these dumb questions, I'm new to Ubuntu and Wine:
1) it seems the Deb package is not ready yet, so the easiest way for a newbie to install it is download the wineloc-0.41.tar.gz file and follow the steps in your first posting?
2) you've mentioned a GUI in your posting, where is it? Does the GUI will show up when you run ./install script?
3) if I don't need languages such as Japanese, Korean, Russian, etc., can I just don't do the steps specific to each language or it'll break the install?

Thanks again for all your help,

---

### Post by michaelbr on 2009-06-28
I tried to follow your instructions from posting 1, when I got to ./ies4linux, I got the following error:
[COLOR="DarkRed"]michael@michael-lt-ubuntu:~/download/ies4linux-2.99.0.1$ ./ies4linux
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

Fontconfig warning: no <cachedir> elements found. Check configuration.
Fontconfig warning: adding <cachedir>/var/cache/fontconfig</cachedir>
Fontconfig warning: adding <cachedir>~/.fontconfig</cachedir>
/home/michael/download/ies4linux-2.99.0.1/ui/pygtk/ies4linux-gtk.py:268: GtkWarning: gtk_text_layout_real_invalidate: assertion `layout->wrap_loop_count == 0' failed
  self.textbuffer.insert_with_tags(self.textbuffer.get_end_iter(), line, tag)
ui/pygtk/python-gtk.sh: line 6:  4264 Segmentation fault      python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py[/COLOR]

What I did wrong? BTW, when I tried to unzip your [http://rs141.rapidshare.com/files/43354195/VeraSansYuanTi.7z](http://rs141.rapidshare.com/files/43354195/VeraSansYuanTi.7z) from Rapidshare, it didn't create a subdir VeraSansYuanTi, so I had to create it manually (I hope this is the correct procedure, it seems based on your further instructions the fonts are installed in subdir VeraSansYuanTi).

ps: my wine version is 1.0.1 and Ubuntu 9.04.

---

### Post by Blue Dolphins on 2009-08-10
I'm having problems with getting wineloc to run, after following all instructions, I tried running an .exe with parenthesis in the path name and the terminal spat out...

bash: error de sintaxis cerca de token no esperado `('  
something like  bash: sintax error on the unanticipated token '(' in english. 

Is there anyway to run a program with a ( in the pathname?  It's a mounted ISO file, so as far as I'm aware there's noway to rename it.

---

### Post by James Keating on 2009-11-28
I couldn't get winelocale to work for me, and the IEs4Linux script only made my Wine setup unusable for the one Japanese program I'm testing, a card designer. (I'm setting up a laptop for my in-laws, and my wife's mother wants to be able to make New Year's cards, but the only thing I can find for Linux is a mediocre program that runs under Adobe AIR.)

After messing up Wine and re-installing it several times, I thought I had found the secret: just change the system language over to Japanese and log back in. 

SadaraX, however, has an even better suggestion -- LANG=ja_JP.UTF-8 wine application.exe -- if you want to run Japanese programs while keeping the main system another language. It works for me when nothing else has. I wish I had read through the whole thread before chasing down unworkable suggestions and general puzzlement elsewhere. 

I do find, however, that on my machine with an English setup, some dialog messages still don't show, while all are fine on the other machine under a Japanese setup.

I didn't even have to change the locale file /var/lib/locales/supported.d/ja or run  dpkg-reconfigure locales. Anthy input through IBus works on the Japanese machine, though Anthy through SCIM fails to put what I write into the program's editing are. I already had all the Japanese fonts, plus msttcorefonts and several fonts I got from my never-used Windows partition (arial-unicode, kozuka gothic, kozuka mincho, osaka, osaka monospace) or off the Web (ms-mincho and ms-gothic from Ricoh). I think that all you need is Wine, the basic fonts and the command. 

Now if I can just get the program to not crash when I open a template card in its proprietary format. (If I just click on one of those templates in Nautilus, wine opens the program with that template showing, just fine. The problem lies in selecting and opening the file.) I've run winetricks and chose most items, but that messed everything up again and I had to start over. I'm going to give it another go or two or three, being selective, until it works or I give up on this program.

---

### Post by Found on 2009-12-03
Thanks for your work.
Looking forward to your deb release :P

Just wanted to add:
Work great, thanks again. Exept of the lines that repeats 4 times before executing any app.
```

err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703

```
What could that be?

---

### Post by amziezelt on 2009-12-10
Hi, I followed the steps as best I could, but when I start up my program, I get this:

> WineLocale 0.41 - CJK Launcher for Wine (cli)
ja_JP
Using locale file /usr/local/share/wineloc/patches/common/ja_JP.reg ...
Setting up Japanese Shift-JIS locale ...
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
Executing application ...
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
fixme:time:GetCalendarInfoW Unimplemented caltype 4
fixme:time:GetCalendarInfoW Unimplemented caltype 3
Restoring old Wine locale settings
fixme:time:GetCalendarInfoW Unimplemented caltype 4
fixme:time:GetCalendarInfoW Unimplemented caltype 3
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703


Anyone have any idea why I'm getting these errors?

Also, Japanese only shows up partially correct in my program... In the bar at the top. The actual text in the body of the program is all gibberish.

---

### Post by DaveBG on 2009-12-24
Hi. Can you explain how do i get the Russian locale and how to use it with Wine?

So i did "touch ru" (probably) but then what to do i put in it using gedit?

Where and how to DL fonts etc?

Please help. I am trying to run Russian version of game Lineage 2 but it cannot run as it gives error "cannot run in this locale" while running it trough wine.

10x

---

### Post by CHaoSlayeR on 2010-02-10
I wanted to do this years ago but I finally did it:

repackaged VeraSansYuanTi and made it available for all at one of my servers:

```
wget http://www.chaoslayer.org/download/VeraSansYuanTi.tar.gz
```

Should be really fast (at least within Europe).


Greetz,
C]-[aoZ

---

### Post by TiGR on 2010-02-28
Please, update your instructions - there is a slight error in step 3. Command "./install" has to be prepended with sharp sign, not with dollar. That is, it has to be executed with superuser rights.

---

### Post by dannymichel on 2010-05-03
is there an updated version to this tutorial?

---

### Post by MikUuser on 2010-05-03
Thank you for your tutorial

---

### Post by dannymichel on 2010-05-03
please be warned that this tutorial completely destroys and previous install of wine; especially if you've set up wine very specifically to work with apps like photoshop cs4

---

### Post by victorfuts on 2010-05-30
hi, thanks for the guide, however the link [http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz](http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz)
seems to be dead, so i stuck in step 1, can you update any link if possible?

---

### Post by roy913 on 2010-07-19
thanks for the post. winelocale seems to be a good program though i have not tried it yet. i use scim with wine and in order to input traditional chinese the way i start my wine program is:
env LC_ALL=zh_CN.UTF-8 wine "C:\Program Files\Microsoft Office\OFFICE11\WINWORD.EXE"

---

### Post by dadim on 2010-12-11
Hi, on Ubuntu 10.04 I could stop after dgkg-reconfigure locale. It seems like things are moving in the right direction.

Many thanks to the Ubuntu team.

---

### Post by mcyan2003 on 2011-02-23
you think will it be able to work on mac as well?
I would certainly hope so since I am using one, yet what would be the changes I need to make?
please let me know, thanks a lot!
If I mss something, forgive and let me know!

---

### Post by opodaniel on 2011-02-26
Hello I just reinstalled my 32.bit Ubuntu 10.10 Maverick and needed to reinstall the Chinese fonts in Wine. So I will take the first post and modify it to reflect the actual situation. The modified post is for Chinese font only.


> **D-- said:**
> 
**Step 1: Getting the Locales**

Execute the following:
```
$ cd /var/lib/locales/supported.d/
# touch zh
```Now open up the three files in a text editor and make certain each contains the following lines.

/var/lib/locales/supported.d/zh
```
zh_CN.UTF-8 UTF-8
zh_TW.UTF-8 UTF-8
zh_CN GB2312
zh_CN.GBK GBK
zh_CN.GB18030 GB18030
zh_TW Big5
```If the lines are there and everything is saved, run:

```
# dpkg-reconfigure locales
```It will throw a warning about SJIS, but trust me, it's OK. Run the command again and everything will say "up-to-date" this time.

Next, prepare for a hellishly long download depending on which fonts you have installed (and if you live in, say, China, like me--our Ubuntu mirror sucks)
[COLOR=Red]I took out the package ttf-saxanami-mincho since I got the error  E: Unable to locate 
[/COLOR]
```
# apt-get install ttf-arphic-ukai ttf-arphic-uming ttf-kochi-gothic ttf-kochi-mincho ttf-mikachan ttf-mona ttf-sazanami-gothic  ttf-vlgothic ttf-alee ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-unfonts ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai ttf-arphic-uming
```Next up, even with all those installed, we will be missing a true Chinese font that handles multiple encodings. Don't suggest any of the AR fonts. It will FAIL on the menu bar of a Wine application. This step is necessary.

We will install Vera Sans YuanTi provided by the Chinese Ubuntu project. Sadly, there's no easy package for this one. We have to do: [B][COLOR=Red]Well this is the tricky part. I have downloaded this package one year before, and don't have the exact link no more, so you will have to Google/Baidu for it yourself. The link here in the code is no longer accesible.

[/COLOR][/B] ```
$ [COLOR=Red]wget http://download.ubuntu.org.cn/software/VeraSansYuanTi.tar.gz[/COLOR]   
$ tar -zxpvf VeraSansYuanTi.tar.gz
# mv VeraSansYuanTi /usr/share/fonts/
# fc-cache -f
# cp /etc/fonts/fonts.conf /etc/fonts/fonts.conf.old
# cp /usr/share/fonts/VeraSansYuanTi/fonts.conf /etc/fonts/
```If you check the INSTALL file of WineLocale, you'll find information about installing Windows fonts. I will leave it out of this guide, because even without those we will get a fully functioning CJK Wine this way If you want the exact same fonts found in Window, follow that part of the guide.

**Step 2: Stealing a nice Wine setup**
  
```
# apt-get update
# apt-get install cabextract wine
$ wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
$ tar zxpvf ies4linux-latest.tar.gz
$ cd ies4linux-*
$ ./ies4linux
```Run the new "ie6" command once and close it. Now do:
$ cp -r ~/.ies4linux/downloads/ie6/* ~/.wine/
[/code]**Step 3: Install WineLocale**

Download WineLocale from my website <http://www.cinnamonpirate.com/software/winelocale/> or grab it with wget:

```
$ wget http://www.cinnamonpirate.com/pub/software/sh/wineloc-0.41.tar.gz
$ tar zxpvf wineloc-0.41.tar.gz
$ cd wineloc-0.41
$ ./install
```This will install the WineLocale default files in /usr/local/share/wineloc and create a symlink in /usr/local/bin. You can now run "wineloc" from anywhere on your system.

**Step 4: Using WineLocale**

WineLocale, at base, is extremely easy to use. The simplest command line is:

```
$ wineloc -l zh_CN /path/to/executable.exe
```-l is the locale flag. If omitted, WineLocale will run it in your current system locale. Valid options are:
[*]ja_JP - Japanese
[*]ko_KR - Korean
[*]zh_CN - Chinese (Simplified)
[*]zh_TW - Chinese (Traditional)

zh_HK and zh_SG will just alias to the other two Chinese modes if you use them. There is also a -o flag that will let you enable DLL overrides (use real DLLs instead of Wine's). This option is tied to a IEs4Linux created Wine setup. If you didn't use theirs, don't touch it or evil magic may happen. Hey, don't complain about "choice": you have the choice not to follow this guide :)

There's also one more option, -f, which lets you specify a different font group. "common" is the default, but there is also a "win" packed in if you followed the guide to install Windows fonts.

You can create your own font themes and overrides if you explore ~/.wineloc/patches, but that's a topic for another guide.

If you followed everything so far, congratulation, you can now run CJK applications in Wine. On launch, the registry will be hacked up to fit your locale. On exit, everything reverts back to the default so your normal Wine applications won't exhibit any odd behavior. If you manage to "crash" it so settings get stuck, you can run this command to reset all font preferences. Ignore any "errors":

```
$ regedit /usr/local/share/wineloc/patches/default.reg
```If you check my website, you can see pictures of CJK applications running using WineLocale. To get your Wine applications looking close to the rest of your UI, you need to use "winecfg". Check section iii of INSTALL, "Configuring Wine with winecfg," to see how to do this.

Have fun :)

---

### Post by pencilcheck on 2011-04-05
for me running on mac all I need is:

```
env LC_ALL=ja_JP.UTF-8 wine executable.exe
```

---

### Post by Gfurst on 2011-07-11
THANKS Pencilcheck, really I've been busting my balls for this, it worked finally the damn installer show japanese letters. Now to the next error "Windows Installer" BLARGH

Anyway, the download for the winelocale is off, and the google apps page completely empty. I wish i had seem this sooner , also it should offer WINEPREFIX support.

---

### Post by jofori89 on 2012-02-12
> $ wineloc -l ja_JP osana.exe
WineLocale 0.41 - CJK Launcher for Wine (cli)
ja_JP
Using locale file /usr/local/share/wineloc/patches/common/ja_JP.reg ...
Setting up Japanese Shift-JIS locale ...
err:module:import_dll Library TDI.SYS (which is needed by L"C:\\windows\\system32\\drivers\\idmtdi.sys") not found
err:winedevice:ServiceMain driver L"IDMTDI" failed to load
wine: cannot find L"C:\\windows\\system32\\plugplay.exe"


I wonder why it always says this even though i installed japanese front and winelocales

and it said this when i run $sudo dpkg-reconfigure locales

>   ja_JP.EUC-JP... hash collision (1716845122) ja_JP.eucjp, ar_OM.utf8
failed
  ja_JP.SJIS... up-to-date
  ja_JP.UTF-8... up-to-date


---

### Post by spark054 on 2012-10-05
Thanks for the HOWTO :D

---

