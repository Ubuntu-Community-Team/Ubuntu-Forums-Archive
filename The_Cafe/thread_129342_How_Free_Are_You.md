---
title: "How Free Are You?"
date: 2006-02-13
forum: The Cafe
---

### Post by Kyral on 2006-02-13
Okay, most of us know one of the awesome things about GNU/Linux is that it is all free, free as in beer. But what about those pesky licenses? 99% of the stuff with Ubuntu is under a GPL-compatible license, so its also Free as in Freedom. But have you ever wondered how Free your system is? Well, your worst nightmare is here..

The VRMS package. VRMS means Virtual Richard M. Stallman. Now for those of you who don't know who RMS is, he is the dude responsible for the GPL and the Free Software Foundation. Also I heard he is VERY hard to get along with. Anyway, check out the output from vrms on my system

```
kyral@AzureDream:~$ vrms
linux-k7                  Complete Linux kernel on AMD K7.
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
linux-restricted-modules- Restricted Linux modules on AMD K7.
nvidia-glx                NVIDIA binary XFree86 4.x/X.Org driver
  Reason: Proprietary license
nvidia-kernel-source      NVIDIA binary kernel module source
rar                       Archiver for .rar files
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
  Reason: Proprietary licence, no source available

 Non-free packages with status other than installed on AzureDream

linux-restricted-modules- ( dei)  Non-free Linux 2.6.12 modules on AMD K7

  14 non-free packages, 0.7% of 1994 installed packages.
kyral@AzureDream:~$
``` 
Bingo..it tells you what isn't FSF complient on your system. Kinda funny. Oyah it also installs itself as a monthly cronjob, but unless you have an MTA installed it won't report to you (I don't think)

So post up your reports!
(Oh for reference, my laptop which runs Debian Sid, is 100% free ;D)

BTW: Flames to /dev/null ;P

---

### Post by cro.smiley on 2006-02-13
Ok so here's mine:

```
smiley@smiley:~$ vrms
               Non-free packages installed on smiley

j2re1.4               Blackdown Java(TM) 2 Runtime Environment, Standard Edi
opera                 The Opera Web Browser

  2 non-free packages, 0.2% of 1255 installed packages.

```

---

### Post by Kyral on 2006-02-13
I got counted twice because linux-k7 contains LRM and thus making it non-free. Its kinda important to me because I'm part of the FSF now...

---

### Post by majikstreet on 2006-02-13
```

majikstreet@oreo:~$ vrms
                Non-free packages installed on oreo

festlex-oald              Festival lexicon from Oxford Advanced Learners' Dictio
festvox-ellpc11k          Castilian Spanish male speaker for Festival
figlet                    Frank, Ian & Glenn's Letters
libmotif3                 Open Motif - shared libraries
linux-386                 Complete Linux kernel on 386.
linux-686                 Complete Linux kernel on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules- Non-free Linux 2.6.10 modules on 386
linux-restricted-modules- Non-free Linux 2.6.10 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.12 modules on 386
linux-restricted-modules- Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.12 modules on 386
linux-restricted-modules- Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.12 modules on 386
linux-restricted-modules- Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
motif-clients             Open Motif - X11 clients (mwm, xmbind)
opera                     The Opera Web Browser
skype                     Free Internet Telephony - The whole world can talk for
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
  Reason: Proprietary licence, no source available

    Non-free packages with status other than installed on oreo

opera-static              ( ins)  The Opera Web Browser

  32 non-free packages, 1.5% of 2160 installed packages.

```
thank god for the code tag.

---

### Post by r4ik on 2006-02-13
For starters no output here.

r4ik@future:~$ vrms
bash: vrms: command not found
r4ik@future:~$ sudo su
root@future:/home/r4ik#  vrms
bash: vrms: command not found
root@future:/home/r4ik#

Is it me ?

O chips its Dapper i am out sorry !

---

### Post by cro.smiley on 2006-02-13
[QUOTE=r4ik]For starters no output here.

r4ik@future:~$ vrms
bash: vrms: command not found
r4ik@future:~$ sudo su
root@future:/home/r4ik#  vrms
bash: vrms: command not found
root@future:/home/r4ik#

Is it me ?[/QUOTE]

Well I'm a starter too but I think you should first install vrms.

Try:
```
sudo apt-get install vrms

```

and then try "vrms".
It should work.

---

### Post by r4ik on 2006-02-13
Thank you here it is,

r4ik@future:~$ vrms
               Non-free packages installed on future

sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)

  1 non-free packages, 0.1% of 1132 installed packages.
r4ik@future:~$

---

### Post by NightwishFreak on 2006-02-13
Here's what VRMS thinks of me...

robert@ripperowens:~$ vrms
No non-free packages installed on ripperowens! rms would be proud.
robert@ripperowens:~$

---

### Post by jasay on 2006-02-13
```
$ vrms
               Non-free packages installed on ubuntu

linux-686                 Complete Linux kernel on PPro/Celeron/PII/PIII/PIV.
linux-686-smp             Complete Linux kernel on PPro/Celeron/PII/PIII/PIV SMP
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Non-free Linux 2.6.15 modules on PPro/Celeron/PII/PIII
linux-restricted-modules- Restricted Linux modules on PPro/Celeron/PII/PIII/PIV.
linux-restricted-modules- Restricted Linux modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
  Reason: Proprietary licence, no source available
xorg-driver-fglrx         Video driver for ATI graphics accelerators

  9 non-free packages, 0.6% of 1554 installed packages.


```Hmmm, by going to synaptic > status > uninstalled (residual config) I was able to knock it down from 24 to 9 packages.  Fighting dirty counting uninstalled packages.[-(

---

### Post by xequence on 2006-02-13
I dont know if anything on my system is under the GPL.

---

### Post by aysiu on 2006-02-13
[A related poll](http://www.ubuntuforums.org/showthread.php?t=95718), in case anyone hasn't voted here yet.

---

### Post by ubuntumaneh on 2006-02-13
This is one of the computers I work with. It is not personal, it is for my fis-math group. I admin it, though

----------------------------------------------------------
sibelius:~> vrms 
vrms: ERROR- Badly formed dpkg-status entry #545!
             pkg=[emacsen-common], pkgstatus=[install ok installed], section=[] 
              Non-free packages installed on sibelius

gsfonts-other             Additional fonts for the ghostscript interpreter
skype                     Skype is free Internet telephony that just works Skype
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
sun-j2sdk1.5              Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)
unrar                     Unarchiver for .rar files (non-free version)

  5 non-free packages, 0.4% of 1343 installed packages.
-------------------------------------------------------------

---

### Post by bonzodog on 2006-02-13
bonzodog@Dwarfstar:~$ vrms
             Non-free packages installed on Dwarfstar

j2re1.4                   Blackdown Java(TM) 2 Runtime Environment, Standard Edition
j2re1.4-mozilla-plugin    Java plugin for mozilla/firefox
linux-restricted-modules- Non-free Linux 2.6.15 modules on x86_64 generic
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
nvidia-glx                NVIDIA binary XFree86 4.x/X.Org driver
  Reason: Proprietary license

  Non-free packages with status other than installed on Dwarfstar

linux-restricted-modules- ( dei)  Non-free Linux 2.6.15 modules on x86_64 generic
linux-restricted-modules- ( dei)  Non-free Linux 2.6.15 modules on x86_64 generic

  7 non-free packages, 0.6% of 1196 installed packages.
bonzodog@Dwarfstar:~$

---

### Post by void_false on 2006-02-13
Where can I get the source for this program? Want to test my system too.

---

### Post by Kyral on 2006-02-13
You can get the source via Apt..but it only works on Debian based distros, as it uses Dpkg's install records to work

---

### Post by bluevoodoo1 on 2006-02-13
brian@ubuntu:~$ vrms
No non-free packages installed on ubuntu!  rms would be proud


HAHA!!!

I don't know how accurate that is though...

---

### Post by Lord Illidan on 2006-02-13
I haven't checked but I am sure that I am not free!! Nvidia, opera (though I don't use it), and java being the main reasons...but who cares?

---

### Post by public_void on 2006-02-13
Non-free packages installed on Laptop

acroread                  Adobe Acrobat Reader: Portable Document Format file vi
acroread-plugins          Plugins for Adobe Acrobat(R) Reader

   Non-free packages with status other than installed on Laptop

doom-wad-shareware        ( pur)
mozilla-acroread          ( dei)  Adobe Acrobat(R) Reader plugin for mozilla / k
  4 non-free packages, 0.3% of 1562 installed packages.

I'm please with mine, the last two aren't installed so why is it 4 non-free packages? I did synaptic > status > uninstalled (residual config).

---

### Post by beercz on 2006-02-13
For what it is worth - here's mine:

> ian@ianpc:~$ vrms
               Non-free packages installed on ianpc

acroread                  Adobe Acrobat Reader: Portable Document Format file vi
fglrx-control             Control panel for the ATI graphics accelerators
fglrx-kernel-source       ATI binary kernel module source
flashplugin-nonfree       Macromedia Flash Player plugin installer
libfaac0                  an AAC audio encoder - library files
libfaad2-0                freeware Advanced Audio Decoder - runtime files
liblame0                  LAME Ain't an MP3 Encoder
libmp4v2-0                MP4 container library - runtime files
libxine-extracodecs       the xine video/media player library, binary files
libxvidcore4              High quality ISO MPEG4 codec library
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
mplayer                   The Ultimate Movie Player For Linux
mplayer-skins             Skins for the Ubuntu mplayer Package
nvidia-kernel-common      NVIDIA binary kernel module common files
realplay                  Supports RealAudio, RealVideo 10, MP3, Ogg Vorbis and
skype                     Free Internet Telephony - The whole world can talk for
xorg-driver-fglrx         Video driver for ATI graphics accelerators
xorg-driver-fglrx-dev     Video driver for ATI graphics accelerators (devel file

    Non-free packages with status other than installed on ianpc

linux-restricted-modules- ( dei)  Non-free Linux 2.6.10 modules on 386
mozilla-acroread          ( dei)  Adobe Acrobat(R) Reader plugin for mozilla / k
mozilla-mplayer           ( dei)  MPlayer-Plugin for Mozilla
mplayer-386               ( dei)  The Ultimate Movie Player For Linux
mplayer-fonts             ( dei)  Fonts for mplayer

  23 non-free packages, 1.3% of 1820 installed packages.

---

### Post by mstlyevil on 2006-02-13
```
An invocation of vrms has been added to the set of cron jobs run on a
monthly basis, so that you will get a periodic reminder of non-free
packages which are installed on your system.  Here is the current list:

               Non-free packages installed on fooker

acroread                  Adobe Acrobat Reader: Portable Document Format file vimozilla-acroread          Adobe Acrobat(R) Reader plugin for mozilla / konqueroropera                     The Opera Web Browser
rar                       Archiver for .rar files
realplay                  Supports RealAudio, RealVideo 10, MP3, Ogg Vorbis and
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
unrar-nonfree             Unarchiver for .rar files (non-free version)

  7 non-free packages, 0.6% of 1271 installed packages.

ozzy@fooker:~$

```

Well I am 0.6% Non-free. I guess that is pretty good from a FOSS standpoint.

---

### Post by shamrock_uk on 2006-02-13
> desktop:~/Simpsons/Season 06$ vrms -e
              Non-free packages installed on desktop

opera                     The Opera Web Browser
realplay                  Supports RealAudio, RealVideo 10, MP3, Ogg Vorbis and
skype                     Free Internet Telephony - The whole world can talk for
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)

  4 non-free packages, 0.3% of 1204 installed packages.

Seems to have missed all my fglrx packages and browser plugins though.

---

### Post by Bandit on 2006-02-13
> No non-free packages installed on stardust!  rms would be proud
How is that for free... :)
Cheers,
Joey

---

### Post by fuscia on 2006-02-13
what is this 'free as in beer' crap? that makes no sense. even cheap beer sucks. i don't get it.

---

### Post by cstudent on 2006-02-13
```


kirby@ubuntu01:~$ vrms
              Non-free packages installed on ubuntu01

abs-guide                 The Advanced Bash-Scripting Guide
acroread                  Adobe Acrobat Reader: Portable Document Format file vimozilla-acroread          Adobe Acrobat(R) Reader plugin for mozilla / konquerorrar                       Archiver for .rar files
realplay                  Supports RealAudio, RealVideo 10, MP3, Ogg Vorbis and
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
sun-j2sdk1.5              Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)unrar-nonfree             Unarchiver for .rar files (non-free version)

  Non-free packages with status other than installed on ubuntu01

opera                     ( pur)

  9 non-free packages, 0.5% of 1698 installed packages.
kirby@ubuntu01:~$


```

1/2% isn't too awfully bad. :)

---

### Post by bored2k on 2006-02-13
Although I don't have it on my pacman repositories (might compile it later), it would most likely crash from the amount of non-free software here.

---

### Post by briancurtin on 2006-02-13
[QUOTE=fuscia]what is this 'free as in beer' crap? that makes no sense. even cheap beer sucks. i don't get it.[/QUOTE]
"free as in beer" means that its free of charge
"free as in freedom" means that the software is free in terms of access to source code and such

---

### Post by fuscia on 2006-02-13
[QUOTE=briancurtin]"free as in beer" means that its free of charge[/QUOTE]

oh! beer's free now? awesome!

---

### Post by akurashy on 2006-02-13
just some thoughts, i really don't care to much about what non-free software i have, i mean you can still download it but the sources isn't for the public. also another thing is that i do like all the freedom thing, but to be honest i'm not a OSS freak or some kind of person that discuss for everything that violates "freedom". 

anyway im not in my computer right now so ican't say @_@

---

### Post by TechSonic on 2006-02-14
```
patrick@techsonic:~$ vrms
             Non-free packages installed on techsonic

acroread                  Adobe Acrobat Reader: Portable Document Format file vimozilla-acroread          Adobe Acrobat(R) Reader plugin for mozilla / konqueroropera                     The Opera Web Browser
rar                       Archiver for .rar files
skype                     Free Internet Telephony - The whole world can talk forsun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
sun-j2sdk1.5              Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)unrar-nonfree             Unarchiver for .rar files (non-free version)

  8 non-free packages, 0.6% of 1268 installed packages.

```

---

### Post by Piggah on 2006-02-14
Heres' mine:

```

nick@nick:~$ vrms
                Non-free packages installed on nick

acroread                  Adobe Acrobat Reader: Portable  Document Format file vi
mozilla-acroread          Adobe Acrobat(R) Reader plugin  for mozilla / konqueror
opera                     The Opera Web Browser
sun-j2re1.5               Java(TM) 2 RE, Standard Editio n, Sun Microsystems(TM)

  4 non-free packages, 0.3% of 1259 installed packages.

```

Not too bad. :P

---

### Post by briancurtin on 2006-02-14
[QUOTE=fuscia]oh! beer's free now? awesome![/QUOTE]
free beer is good beer*



* usually only while you are drinking it

---

### Post by fuscia on 2006-02-14
[QUOTE=briancurtin]free beer is good beer*

* usually only while you are drinking it[/QUOTE]

alright...temptation must be quenched. brb.

---

### Post by mckryptyk on 2006-02-14
Hi guys! I saw this thread and gave it a try look at this :)

:-# @dremora:~$ vrms
              Non-free packages installed on dremora

unrar-nonfree             Unarchiver for .rar files (non-free version)

  1 non-free packages, 0.1% of 1158 installed packages.

Must be a mistake 'cuz I thought I installed nvidia-glx ? Oh well, I'm happy with what it says :)

---

### Post by Krigl on 2006-02-14
krigl@Megatherion:~$ vrms
            Non-free packages installed on Megatherion

grokking-the-gimp         GIMP tutorial book by Carey Bunks (HTML)
lha                       lzh archiver
rar                       Archiver for .rar files
unrar-nonfree             Unarchiver for .rar files (non-free version)

  4 non-free packages, 0.2% of 1766 installed packages.


Hmm, not bad - I'm 99,8% free. Might be a good parole for a T-shirt.

---

### Post by eriqk on 2006-02-14
It seems vrms isn't looking hard enough. It claims I have no non-free packages installed, but it's overlooking Flash, Sun Java, w32 and a couple of bits and bobs here and there.

Groet, Erik

---

### Post by mattheweast on 2006-02-14
[QUOTE=eriqk]It seems vrms isn't looking hard enough. It claims I have no non-free packages installed, but it's overlooking Flash, Sun Java, w32 and a couple of bits and bobs here and there.
[/QUOTE]

Yeah, I confirm that this program doesn't actually work. I have loads of restricted modules packages installed, and vrms does not show them at all.

Matt

---

### Post by akurashy on 2006-02-14
Non-free packages installed on akulinux

linux-386                 Complete Linux kernel on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.15 modules on AMD K7
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules helper script
nvidia-glx                NVIDIA binary XFree86 4.x/X.Org driver
  Reason: Proprietary license
sun-j2re1.5               Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
  Reason: Proprietary licence, no source available

  Non-free packages with status other than installed on akulinux

linux-restricted-modules- ( dei)  Non-free Linux 2.6.15 modules on 386

  10 non-free packages, 0.7% of 1440 installed packages.


there we go!, though flash isn't there ._.

---

