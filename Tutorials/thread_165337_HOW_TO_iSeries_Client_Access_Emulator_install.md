---
title: "HOW TO: iSeries Client Access Emulator install"
date: 2006-04-24
forum: Tutorials
---

### Post by n8bounds on 2006-04-24
[B][COLOR="Red"][SIZE="4"]EDIT on 2012-02-21: see [http://sourceforge.net/projects/ibm5250onubuntu/](http://sourceforge.net/projects/ibm5250onubuntu/)[/SIZE]
[/COLOR][/B]


EDIT on 20110510: [http://n8.thruhere.net/blog/?p=1122]("http://n8.thruhere.net/blog/?p=1122")

Updated for Natty. Basic idea is that Natty also needs xfonts-100dpi xfonts-75dpi and a reboot.


UPDATED 20100720

IBM releases RPM binaries for this official PC5250 client intended for use with RHEL, and then only for their 32 bit architecture. The following is how I got it installed and working on Ubuntu 10.04 AMD64.

Download the 32 bit version of System i Access from IBM: [http://ibm.com/systems/i/software/access/linux/downloads.html](http://ibm.com/systems/i/software/access/linux/downloads.html)

Install the following packages:

alien odbcinst1debian1 unixodbc libmotif3 msttcorefonts ttf-mscorefonts-installer ia32-libs

You need the 32 bit lib of libstdc++5 which you can extract from an old DEB, say this one: [http://packages.ubuntu.com/hardy/i386/libstdc++5/download](http://packages.ubuntu.com/hardy/i386/libstdc++5/download) or by using this direct command (if this hotlink doesn’t die):

wget [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu4_i386.deb)

Extract the files from that deb and put it where IBM5250 needs it:

ar vx libstdc++5*.deb; tar xzf data.tar.gz; sudo mkdir /usr/lib32; sudo mv usr/lib/libstdc++.so.* /usr/lib32; ls -la /usr/lib32/ | grep libstdc++.so.5

Now do the same thing for libmotif3 (remember to get the 32bit version) which you can find here:

[http://packages.ubuntu.com/hardy/i386/libmotif3/download](http://packages.ubuntu.com/hardy/i386/libmotif3/download)

Or use this direct link:

wget [http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb)

Again, extract the files and such:

ar vx libmotif3*.deb; tar xzf data.tar.gz; sudo mkdir /usr/lib32; sudo mv usr/lib/libXm.so.3* /usr/lib32; ls -la /usr/lib32/ | grep libXm.so.3

Change directories and use alien on the RPM:

sudo alien –scripts -g iSeriesAccess-*.rpm

This will make a dir containing the package contents from the rpm in debianizable form. Change directory into the one that doesn’t have the “.orig” on it (such as ./iSeriesAccess-6.1.0) and run this command (dpkg-buildpackage should already be installed):

sudo dpkg-buildpackage -b -d -ai386

Ensure your locale is generated. I use en_US, so I ran this command:

sudo locale-gen en_US

Change dirs up one then install the resulting deb:

sudo dpkg -i –force-architecture iseriesaccess_*.deb

FINALLY, you’re finished. You can launch the emulator like this:

ibm5250 192.168.156.whatever -title MyFancyTitleBar -DISPLAY_NAME “UBUNTUA UBUNTUB UBUNTUC UBUNTUD” -LANGID en_US

UPDATE: I wrote a script that will do all this for you. All you need is my script and the RPM from IBM (which I also happen to have), get them here:
[http://n8.thruhere.net/export/free/ibm5250/](http://n8.thruhere.net/export/free/ibm5250/)
Just put the script and the RPM in the same dir, get a terminal in that dir, chmod +x the script and run the script, passing the filename of the rpm to it as the first argument. The script works both in 32 and 64 bit Ubuntu 10.04.

Careful with quotes and such when using copy/paste. Best to just download the script. Also. 5.4 seems to work better than 6.1 for me :)

[http://n8.thruhere.net/blog/?p=142](http://n8.thruhere.net/blog/?p=142)


Here's the script
```

#!/bin/bash


function usagedie {
        echo '' 1>&2
        echo "iSeries Client Access RPM Installer for Ubuntu" 1>&2
        echo "Usage: $0 <filename.rpm>" 1>&2
	echo "Example: $0 iSeriesAccess-6.1.0-1.0.i386.rpm" 1>&2
        echo '' 1>&2
	exit
}

function installit64 {
	sudo aptitude install alien odbcinst1debian1 unixodbc libmotif3 msttcorefonts ttf-mscorefonts-installer ia32-libs -y

	if [ -d /usr/lib32 ]; then
		echo ''
	else
		sudo mkdir /usr/lib32
	fi

	wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu4_i386.deb
	wget http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb

	ar vx libstdc++5_3.3.6-15ubuntu4_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libstdc++.so.* /usr/lib32;
	ar vx libmotif3_2.2.3-2_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libXm.so.3* /usr/lib32;

	sudo alien --scripts -g $TARGETRPM
	cd iSeriesAccess-*
	sudo dpkg-buildpackage -b -d -ai386
	sudo locale-gen en_US
	cd ..
	sudo dpkg -i --force-architecture iseriesaccess_*.deb
}

function installit32 {
	sudo aptitude install alien odbcinst1debian1 unixodbc libmotif3 msttcorefonts ttf-mscorefonts-installer -y

	wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu4_i386.deb
	wget http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb

	ar vx libstdc++5_3.3.6-15ubuntu4_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libstdc++.so.* /usr/lib;
	ar vx libmotif3_2.2.3-2_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libXm.so.3* /usr/lib;

	sudo alien --scripts -g $TARGETRPM
	cd iSeriesAccess-*
	sudo dpkg-buildpackage -b -d -ai386
	sudo locale-gen en_US
	cd ..
	sudo dpkg -i iseriesaccess_*.deb
}

function cleanup {
	cd ..
	sudo rm -rf tmpiseriesrpm
}

function goodbye {
	echo ''
	echo "Script complete!"
	echo ''
	echo "Launch the program like this:"
	echo "ibm5250 192.168.156.whatever -title MyFancyTitleBar -DISPLAY_NAME \"UBUNTUA UBUNTUB UBUNTUC UBUNTUD\" -LANGID en_US"
	echo ''
	echo "Uninstall the program like this:"
	echo "sudo dpkg --remove iseriesaccess"
	echo ''
}

if [ "$1" == "" ]; then
        usagedie
fi

TARGETRPM=$1

if [ -d tmpiseriesrpm ]; then
        sudo rm -rf tmpiseriesrpm
else
	echo ''
fi

mkdir tmpiseriesrpm
cp $TARGETRPM tmpiseriesrpm
cd tmpiseriesrpm

MYARCH=`uname -m`

if [ "$MYARCH" == "x86_64" ]; then
	installit64
else
	installit32
fi

cleanup
goodbye

```

---

### Post by USRPRF on 2006-05-24
Hi

Ok that allow you to launch ibm5250 and create a session with a QPADEV DISPLAY_NAME. But what is more useful in iSeriesAccess for linux is setup5250 that allow you to create several (up to 99) sessions, each with a specific device name. Actually i installed iseriesaccess on FC5 and made it works, and i noticed that without setup5250 you are unabel to connect to an iSeries with device restriction (in that case you can't allow anonymous users to connect with QPADEVXXXX). If i try to run setup5250 i get the following errors:
```
setup5250: [ ERROR ]: Xt Warning: locale not supported by C library, locale unchanged.
setup5250: [ ERROR ]: Xt Warning: Missing charsets in String to FontSet conversion.

```

Does anyone know how to handle this? I searched on the net but i didnt find anything.

Thanks

---

### Post by mdfel on 2006-06-14
finally made a complete iSeries Access for linux "localized" install. 
it all starts with the fact that iSeries Access doesn't support UTF-8 locales, so that's what i did:
consider that I'm connecting to an iseries host with CCSID = 1144 from a ubuntu 6.06 and i'm italian.
Please use at least version 1.14 of iSeries Access for linux, for it adds the -USE-CP directive

Please use your appropriate language identifiers:
```
cd /opt/ibm/iSeriesAccess/mri
sudo ln -s /opt/ibm/iSeriesAccess/mri/it/ it_IT
```

then add iso8859-1 support to the appropriate file (in my case it):
```
sudo gedit /var/lib/locales/supported.d/it
```
and append the line: 
```
it_IT.ISO-8859-1 ISO-8859-1
```

then execute the command:
```
sudo locale-gen
```

now you have to start any ibm iseries application by redefining the LANG variable, so i created the bash script:
```
#!/bin/bash
LANG=it_IT.ISO-8859-1
/opt/ibm/iSeriesAccess/bin/setup5250 -USE-CP1144
```

please note that in order to use setup5250 you probably have first to add /opt/ibm/iSeriesAccess/bin to PATH. I also configured ldconfig for ibm libs

Hope this helps

---

### Post by rgriffin on 2006-10-27
This is the bomb. Thanks for posting the very helpful how-to ;)

---

### Post by elvisd on 2006-10-31
Thank you for completing my thread. I'll link this thread on my blog... elvisd.blogspot.com

---

### Post by Popcorn12k on 2006-11-15
I too am trying to install iseries Access on Dapper.  I have followed the instructions provided by both elvisd, sirnigel and n8bound.  When I get to this command 

sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/ libcwbcore.so

I get this response:
ln: target `libcwbcore.so' is not a directory

If I continue through the configuration I get this response when I try to start the application:

ibm5250: error while loading shared libraries: libcwbcore.so: cannot open  shared object file: No such file or directory

I think I have a broken link; however, I don't know why nor how to fix it.  Any help would be appreciated.

---

### Post by n8bounds on 2006-11-19
> **Popcorn12k said:**
> I too am trying to install iseries Access on Dapper.  I have followed the instructions provided by both elvisd, sirnigel and n8bound.  When I get to this command 

sudo ln -s /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/ libcwbcore.so

I get this response:
ln: target `libcwbcore.so' is not a directory

If you used the clipboard on that post, you have a SPACE betweeen /usr/lib and libcwbcore.so on the tail of your command there.

---

### Post by Circus-Killer on 2006-12-06
i've followed all the instructions in this thread, but i'm still getting the following error:

5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-19-*-75-75-m-*" to type FontSet.

anyone know a solution?

---

### Post by n8bounds on 2006-12-11
> **Circus-Killer said:**
> i've followed all the instructions in this thread, but i'm still getting the following error:

5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-19-*-75-75-m-*" to type FontSet.

anyone know a solution?

Do you have the MS Fonts installed?  If you have Universe and Multiverse repositories enabled, I think you can add them via the Add/Remove tool (or synaptics).  Alternatively, you could try the Automatix2 scripts.  I think I saw something in there about MS Core Fonts.

Cheers

---

### Post by Circus-Killer on 2006-12-11
yes, ms fonts is already installed, that is not the problem.

---

### Post by Mario Rossi on 2006-12-13
Same problem for me. When I try to execute the command 'ibm5250' I have these error messages:
5250: [ INFORMATIONAL ]: Build Date: September 2006 (1.2).
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-24-*-75-75-m-*" to type FontSet.

Ubuntu 6.10 with IBM-Client-access 5.4.02

Any suggestion?.

---

### Post by n8bounds on 2006-12-18
You guys arent running EDGY are you..?

---

### Post by Circus-Killer on 2006-12-18
> **n8bounds said:**
> You guys arent running EDGY are you..?

yes, i am.

---

### Post by Circus-Killer on 2006-12-21
n8bounds, perhaps if you still have the .rpm of the version you used (i noticed its a couple of versions behind) we can try it out. could be specific problem with the version we are trying. (im using the same one as mario)

---

### Post by ColdBeer on 2007-01-04
I found the solution :twisted:, because iSeries Access for linux seems to need the xfs font server](*,) :

```
$ sudo aptitude install xfs
$ sudo gedit /etc/X11/xorg.conf
```

Add, into the Section "Files" (between "Section" and "EndSection" this line:

```
        FontPath        "unix/:7100"
```

restart X (or the system) and try your setup5250 or ibm5250.:D

---

### Post by Circus-Killer on 2007-01-04
unfortunetly, i'm at work, and will have to wait till i get home before i try out the solution (if i have time).

i will post back as soon as i've tried it out.
thanks for the help. ;)

---

### Post by Circus-Killer on 2007-01-11
awesome, it worked ColdBeer, thanks a heap :D.

the only thing i did differently was when n8bounds sais to issue the following command:
> sudo alien -i iSeriesAccess-5.2.0-1.10.i386.rpm

i found it only worked when i issued it like so:
> sudo alien -ic iSeriesAccess-5.2.0-1.10.i386.rpm

the rest of the howto, plus your fix ColdBeer, works like a charm. well, at least getting into the system, now i just gotta see if the printing will work. i'll get back to you on that one, but to be honest, i have huge doubts on printing working properly.

---

### Post by ColdBeer on 2007-01-11
> **Circus-Killer said:**
> awesome, it worked ColdBeer, thanks a heap :D.Not at all :rolleyes: 

> **Circus-Killer said:**
> the only thing i did differently was when n8bounds sais to issue the following command...

I did:
```
$ sudo aptitude install msttcorefonts alien xfs libmotif3 libxaw6 libstdc++5
$ sudo fc-cache -f -v
$ sudo gedit /etc/X11/xorg.conf
(add <<FontPath "unix/:7100">> in the files section)
$ sudo alien -dc iSeriesAccess-5.4.0-1.2.i386.rpm
(in this way, I maintain the .deb file for future uses)
$ sudo dpkg -i iseriesaccess-5.4.0-2.2.i386.deb
$ sudo ln -s /opt/ibm/iSeriesAccess/lib/*.so /usr/lib/
$ sudo reboot
(to apply the changes in the font server)
```> **Circus-Killer said:**
> ...now i just gotta see if the printing will work. i'll get back to you on that one, but to be honest, i have huge doubts on printing working properly.

I prefer to use LPD or better [SIZE=4][COLOR=DarkGreen]**IPP**[/COLOR][/SIZE] (as [SIZE=3][COLOR=Navy]_**[IBM recommends]("http://publib.boulder.ibm.com/infocenter/iseries/v5r4/topic/rzalu/rzaluconippprt.htm#rzaluconippprt")**_[/COLOR][/SIZE]) to use any printer in the network.

---

### Post by Circus-Killer on 2007-01-11
(double post, sorry)

---

### Post by Circus-Killer on 2007-01-11
> I prefer to use LPD or better [SIZE=4][COLOR=DarkGreen]**IPP**[/COLOR][/SIZE] (as [SIZE=3][COLOR=Navy]_**[IBM recommends]("http://publib.boulder.ibm.com/infocenter/iseries/v5r4/topic/rzalu/rzaluconippprt.htm#rzaluconippprt")**_[/COLOR][/SIZE]) to use any printer in the network.

okay, i'm not to sure what either of those is, but let me explain my problem and maybe you can help me find the right path.

basically, my folks usually connect to an AS400 server using iseries access for windows. now being a typical ubuntu user, i would like to see if my parents would like the switch (and im sure they will).

anyways, with the iseries access for windows, when setting up emulator sessions, there is an option to set it as a *display* session or as a *printer* session. with the printer session setting, more options become available about printing. then whenever you need to print, you have to have the print session running in the background (and obviously you would still be in the display section requesting the print).

now, how do i go about printing in much the same way, or at all. to be honest, i havent given printing a complete try, but as i said, i'll come back to yah with my failed attempts.

---

### Post by smackcode on 2007-01-12
i get this  when i run ibm5250--> ./ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory

any ideas?

---

### Post by Circus-Killer on 2007-01-12
did you create the necessary link:
> sudo ln -s /usr/X11R6/lib/libXm.so.3 /usr/lib/libXm.so.3

---

### Post by ColdBeer on 2007-01-12
> **Circus-Killer said:**
> anyways, with the iseries access for windows, when setting up emulator sessions, there is an option to set it as a *display* session or as a *printer* session. with the printer session setting, more options become available about printing. then whenever you need to print, you have to have the print session running in the background (and obviously you would still be in the display section requesting the print).

now, how do i go about printing in much the same way, or at all. to be honest, i havent given printing a complete try, but as i said, i'll come back to yah with my failed attempts.

Sincerely, Circus: IBM is not working on this way and letting printer emulation dies. The future (and in my way of thinking: the PRESENT) is to use the standards and, LPR and IPP are the standards actually.

You need NOTHING to configure IPP on your Ubuntu installation, because GRUB use it by default. The only thing you need is to configure the printer -easy- on the AS/400 as a remote IPP printer (remote host, name of the remote queue -your printer name- and port -631-). Now, you will not have errors or stopped queues because the user forgetted to open the printer emulation, or he stopped it. In the same way, your AS/400 will not depend of the configuration -or transform- in the emulator. You could configure the printer in the AS/400 as PCL or Postcript and have EXACTLY the print you want.

Remember: Windows XP and 2000 use IPP and LPD in the same way, so you just need to configure one printer that will work in the same computer independently of the OS you started in that host.

By the same reasons, as soon as you have less "things" between your host -AS/400- and your printer, you will have less problems and, of course, less troubles to detect an error.

So, resuming: Your parents will don't need anymore to open a printer emulation session; your AS/400 will print reports in the PC with just one requirement (it must be on); you will have less problems with transforms and report formats; you will have less work to configure it...

PD: Sorry, my english is not my best knowledge ;-) But I have some experience with AS/400 and a variety of systems interconected, so it could be a nice thing for me if I could help you with this or other things about them. Specially, if we still talk about Ubuntu:mrgreen:

---

### Post by smackcode on 2007-01-12
@circus-killer: hmmm i just noticed that libmotif3 wasn't installed. I can't seem to find the package when i use aptitude. Which repository does libmotif3 reside?

Update: i think i got it already, we'll see if this works. thanks guys

---

### Post by Circus-Killer on 2007-01-12
> **ColdBeer said:**
> Sincerely, Circus: IBM is not working on this way and letting printer emulation dies. The future (and in my way of thinking: the PRESENT) is to use the standards and, LPR and IPP are the standards actually.

You need NOTHING to configure IPP on your Ubuntu installation, because GRUB use it by default. The only thing you need is to configure the printer -easy- on the AS/400 as a remote IPP printer (remote host, name of the remote queue -your printer name- and port -631-). Now, you will not have errors or stopped queues because the user forgetted to open the printer emulation, or he stopped it. In the same way, your AS/400 will not depend of the configuration -or transform- in the emulator. You could configure the printer in the AS/400 as PCL or Postcript and have EXACTLY the print you want.

Remember: Windows XP and 2000 use IPP and LPD in the same way, so you just need to configure one printer that will work in the same computer independently of the OS you started in that host.

By the same reasons, as soon as you have less "things" between your host -AS/400- and your printer, you will have less problems and, of course, less troubles to detect an error.

So, resuming: Your parents will don't need anymore to open a printer emulation session; your AS/400 will print reports in the PC with just one requirement (it must be on); you will have less problems with transforms and report formats; you will have less work to configure it...

PD: Sorry, my english is not my best knowledge ;-) But I have some experience with AS/400 and a variety of systems interconected, so it could be a nice thing for me if I could help you with this or other things about them. Specially, if we still talk about Ubuntu:mrgreen:

dont worry about your english, its very good! and thanks for all your help. you do indeed seem very knowledgeable on the subject of AS/400. ;) 

my worry about the whole printing thing is this. if i'm not mistaken, you are talking about screen printing, which would just print the current display (correct me if i'm wrong). 

the problem is, that my folks need to type in a whole LOT of orders. afterwards, they give the command to print, and ALL the orders (sent from the server to the printer emulation session) print in one go (much better than having going screen to screen for each order). which doesnt make sense to me, so i'm sure i got this wrong. but when i try print, the emulator spews out a bunch of errors such as: 

> 
Job ******/******/QPADEV0001 started on 12/01/07 at 17:37:23 in subsystem QI
 Error message CPF4131 appeared during OPEN (C S D F).
 C
 RPG9001 received by RPS099CL at 400. (C D I R)
 C
 CEE9901 received by CALLQK at 3300. (C D I R)
 C
 CPF9999 received by AGMENUECL at 500. (C D I R) 


also, if i try do a screen print, i get the following error:

> 
printer did not respond.
please make sure it is ready to print.


and yes, my printer is on with paper and work and is plugged in and etc. etc.
so as you can see, i'm at a complete loss, and i dont see much prospect of getting the printing right. what i dont understand is why they make it so different from windows. in windows you can create a printer session, so why not in linux.

anyways, i dont know, i'm just lost. ](*,) anymore help you can dish is appreciated. :)

---

### Post by Circus-Killer on 2007-01-12
if all you need is terminal access, man do i have the solution for you. a thousand times easier than installing iseries access for linux. try out tn5250:

> sudo apt-get install tn5250

then type in:

> tn5250 ip.add.re.ss

could it be anymore easier than that. :D 
still cant print though, so neither helps me much.

tried out tn5250j, but thats too much of a mission. tn5250 is the way to go in my opinion, give it a bash.

---

### Post by ColdBeer on 2007-01-15
> **Circus-Killer said:**
> dont worry about your english, its very good! and thanks for all your help. you do indeed seem very knowledgeable on the subject of AS/400. ;) 

my worry about the whole printing thing is this. if i'm not mistaken, you are talking about screen printing, which would just print the current display (correct me if i'm wrong).
Not, Circus... this is your mistake. I'm talking about creating a remote printer in the AS/400 which will be always "ready to print". When programming in the AS/400 and wanna print a report, you assign a "queue" for that job. That queue is assigned to a printer (local printer, 5250 -emulated or real- printer, or net printer -HP net printer, LPR, IPP...-). Of course, this queue could be stopped if the printer can't be located.

Talking about the "screen printing", there are two ways for -each- the same job: local print (which means that your emulation software make the job using only local recourses) and host printing (you give to the AS/400 -which knows too what's your screen showing- the job, which will be worked as any print job in the AS/400 queue. It knows what's your default printer because it's declared in the session). In the first way, for example, you could print your screen in a printer that is not knowed by the AS/400. In the second way, the printer MUST BE defined in the AS/400 and asigned to your session definition ([FONT="Courier New"]wc *dev TERM01[/FONT], for example).

So, if I explained right, you could understand that must separate the printer, the queue, the printer device, and the way you print (emulation, LPR, IPP, HP-net...) but you must NEVER confuse a "local screen printing" because it's not related to your AS/400.

> **Circus-Killer said:**
> and yes, my printer is on with paper and work and is plugged in and etc. etc.
so as you can see, i'm at a complete loss, and i dont see much prospect of getting the printing right. what i dont understand is why they make it so different from windows. in windows you can create a printer session, so why not in linux.
It's true, you could create a printer session in Windows, but I tell you: I have more than 200 PCs with AS/400 emulation, but only 4 of them use printer emulation. We use the LPR way because it gives much less work for us -the net admins-, less work for the user -which doesn't need to remember opening the printer session, and less work for the AS/400 and the network traffic. And, remember which I told you before: IBM Client Access for Windows still use the printer emulator just for time compatibility reasons. They recommend to use the other ways because printer emulation is an old and bad way of printing.

Newer operating systems (Win 2k, XP, Linux...) uses modern (well, they are really old, but this is another discussion) ways of printing. So, I could recommend you to use them too.

I think it could be better to talk with your AS/400 system administrator and tell him about this. I'm sure he will prefer the way I tell you.

If you are still confused please, let me know and I could try to help you. ;-)

... Sorry, I forgeted your last post:

TN5250 is another way of 5250 terminal emulation, but it is less -and more difficult- advanced. You have less configuration and -in my knowledge- it can't use secure sessions.

In the other way, IBM Client Access for Linux has a BIG thing TN5250 doesn't: ODBC connection. With them, you could work in your OpenOffice Calc -or Base, or Writer- directly with your AS/400 data.

Remember that IBM Client Access for Windows is based in an OLD developing, so it still maintain -for compatiblity- old programs that in a modern way of work are not needed: printer emulation (forget it, it's an stupid way of printing, full of problems with the final print, the transform, the drivers...), the AS/400 data transfers (RTOPC, RFROMPC... which are completelly out of the XXI century since FTP and SAMBA exists) and a lot of other options which are in the Client Access for Windows package since Windows 3.0.

---

### Post by kelboy on 2007-01-25
first post here...so be gentle...
found a couple of things...
for those people getting XT errors...
[B]5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-24-*-*-*-m-*" to type FontSet.
[/B]
first set the Xorg.conf
to correct fonts(or at least more fonts.

add 
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
to the [B]sudo gedit /etc/X11/xorg.conf
[/B]

then restart x [cntrl+alt+backspace]
see if it works...I say this because it worked for me for a while till i tried to determine what actually fixed the above error...

if it doesn't work run **xset fp**

and then try  /opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_us
to start the client access session....

just as a note there is also a new RPM client access package out there
* iSeriesAccess-5.2.0-1.6.i386.rpm*

I commented out the above lines in my xorg.conf and it broke my client access with the 
XT error FontSet conversion error...

and then fixed it by running  **xset fp**

hope this helps someone out...

thanks to all the at posted this howto it almost worked several times. 
once I entered the the above Fontpaths and ran xset fp, i could consistantly break it with the fontset coversion error and fix it again...

kel

---

### Post by Circus-Killer on 2007-01-26
> **kelboy said:**
> first post here...so be gentle...
found a couple of things...
for those people getting XT errors...
[B]5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Cannot convert string "-*-lucidatypewriter-medium-r-normal-*-24-*-*-*-m-*" to type FontSet.
[/B]
first set the Xorg.conf
to correct fonts(or at least more fonts.

add 
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
to the [B]sudo gedit /etc/X11/xorg.conf
[/B]

then restart x [cntrl+alt+backspace]
see if it works...I say this because it worked for me for a while till i tried to determine what actually fixed the above error...

if it doesn't work run **xset fp**

and then try  /opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_us
to start the client access session....

just as a note there is also a new RPM client access package out there
* iSeriesAccess-5.2.0-1.6.i386.rpm*

I commented out the above lines in my xorg.conf and it broke my client access with the 
XT error FontSet conversion error...

and then fixed it by running  **xset fp**

hope this helps someone out...

thanks to all the at posted this howto it almost worked several times. 
once I entered the the above Fontpaths and ran xset fp, i could consistantly break it with the fontset coversion error and fix it again...

kel

well, i dont know about your method, but if you read this whole thread you will have seen whe got passed the problem of the fonts. read the posts in this thread that mention installing xfs and editing xorg appropriately. its the easiest way to get iseries working.

---

### Post by pjnofrills on 2007-01-26
Hey everyone.  I'm relatively new to Ubuntu, and I really was excited to see that people have gotten iSeries Access for Linux working.  It would be great for me to access the iSeries at work.  I finally got setup5250 to launch, but it's not saving my options, and it gives this error if I try to launch a session from the menu:
 
setup5250: [ ERROR ]: Unable to make directory: /root/.iSeriesAccess/ibm_5250. errno = 2. create_mode = 1ff.
setup5250: [ ERROR ]: shmget failed. errno = 2, key = 71077346, size = 536.
bash: ibm5250: command not found

What did I do?
It's probably really simple, I just barely know how to set permissions.  I'm still trying to remember bash commands from college.

I really want to use Ubuntu for obvious reasons, but if I can't figure this out I will have to go RedHat or something similar (gasp!)..

Thanks!

---

### Post by kelboy on 2007-01-26
> **Circus-Killer said:**
> well, i dont know about your method, but if you read this whole thread you will have seen whe got passed the problem of the fonts. read the posts in this thread that mention installing xfs and editing xorg appropriately. its the easiest way to get iseries working.

Yah I did the entire post and all the tips and howto's of it...
[U]Unfortunately Like i said I had it working, 
and then I  broke the launcher [by commenting out 3 Fontpath lines in Xorg.conf] when i tried to determine which "change I did actually got it working" 
I was trying to document it for impletation at our some of our offices.[/U]
. i'm a programmer and i like to know what fixes something when it breaks and what broke it. unfortunately with linux, that seems difficult. 
Regardless, I had xfs installed, and just adding the unix:7000 was not enough on 1 machine to get it working, i had to add the additional font paths. believe me i did this entire howto on 2 different machines, 1 worked 1 didn't. [both identical settings xorg/symbolic links/steps to install/logs/etc..
Frustrating is an understatement...

1 other thing I did do was to look at the xorg.0.log [Administration->System Logs->Xorg.0.log]
saw several errors pointing to fonts,such as
**(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".**
	**Entry deleted from font path.**
	**(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").**
I ran mkfontdir as the log suggested on each of these errors, 
and then re-ran
  [B]sudo fc-cache -f -v
[/B]

Like I said before I just was pleased to get it back and working, and i still don't know definitivly what actually fixed the fontconversion errors...Client Access seems to be a fragile egg on Ubuntu, I expect it to break again,eventually.

I do genuinely appreciate all the effort made in this post and all others associated with ubuntuforums, i added these because they helped my situation and may help some else also....
thanks again
kel

---

### Post by n8bounds on 2007-02-23
I GOT IT!!  THIS WORKS ON A FRESH INSTALL OF EDGY!!

Just open up your repos and do this:





DO AS ROOT



apt-get install msttcorefonts -y



fc-cache -f -v



apt-get install libmotif3 libxaw6 libstdc++5 alien -y



alien -i iSeriesAccess-5.4.0-1.0.i386.rpm  -cv





DO AS NOTROOT



xset fp



(just once as far as I can tell, not necessary every time)





THIS IS THE COMMAND EXAMPLE, PLEASE CHANGE IT BEFORE USING IT (THE GEOMETRY IS FINE HOW IT IS JUST FYI)


ibm5250 192.168.1.1 -geometry 9999x9999+0+0 -title LinuxCanWorkTheFourHundred -DISPLAY_NAME "PCNAMEA PCNAMEB PCNAMEC" -LANGID en_US




NOTE:

Rumor has it that you may need to run the



xset fp



...command again later...after something changes...somewhere, just for future reference, but I havent had to yet


I'd attach the exact version RPM I used, but this thing wont let me....

---

### Post by n8bounds on 2007-02-23
**I have a full recap of a working solution for iSeriesAccess-5.4.0-1.0.i386.rpm on 6.10 Edgy here:**

[http://ubuntuforums.org/showthread.php?p=2202667](http://ubuntuforums.org/showthread.php?p=2202667)

---

### Post by angelusdad on 2007-06-12
hello !!!!

i'm trying to install ibm client, i follow the instruction in this post, but when i start  the ibm client, with  the command ibm5250 the terminal  show an error :

alessandro@alessandro-desktop:~$ ibm5250
5250: [ INFORMATIONAL ]: Build Date: September 2006 (1.2).
5250: [ ERROR ]: Locale invalid: it_IT.UTF-8 = 0x2B697469 was not found in localeList. Defaulting to en_US
5250: [ ERROR ]: Locale invalid: it_IT.UTF-8 = 0x2B697469 was not found in localeList. Defaulting to en_US
5250: [ ERROR ]: Locale invalid: it_IT.UTF-8 = 0x2B697469 was not found in localeList. Defaulting to en_US


then window appears and i can write the remote ip machine with username and password, i push enter and on the terminal appear another error:

5250: [ ERROR ]: Start Up Confirmation Response  = 0xF8 0xF9 0xF4 0xF0 = Automatic configuration failed or not allowed.
5250: [ ERROR ]: NSC0053: Telnet::getdata(): recv() returned 0.


what the problem can anybody help me??? thanks

---

### Post by AlbertoT on 2007-08-23
Hello

I've followed your instructions and my iSeries Access runs OK. (Thanks!!)

My problem it's the ODBC connection and PHP. I've setup a conection with ODBCConfig, but when I open a test PHP file the system show this message:

Fatal error: Call to undefined function odbc_connect() in /var/www/testodbc.php on line 3

I've PHP5 (and the package phpODBC) and Apache2 and runs OK

The only strange thing it's that PHPInfo() doesn't show any information about ODBC

---

### Post by ColdBeer on 2007-08-24
Sorry, but I never tested iSeries ODBC connection. :-(

---

### Post by n8bounds on 2008-04-12
I made a deb!

[http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb](http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb)

---

### Post by Circus-Killer on 2008-04-14
haven't tested it yet, but just awsome that you giving packaging a try ;)

---

### Post by simplysimple on 2008-05-14
Anybody try this out on 8.04....or know if it can be done?

---

### Post by simplysimple on 2008-05-19
bump...i'll give it a run on 8.04 and let you know what i come up with. :)

---

### Post by simplysimple on 2008-05-19
followed the instructions to install the rpm on 8.04(32bit) the only difference was the version which was iSeriesAccess-5.4.0-1.**6**.i386.rpm

worked like a charm...i used 'setup5250' in the terminal to configure everything and then created a launcher to run 'ibm5250' for convenience. 

thanks for the guide!!

---

### Post by captainkirk on 2008-08-22
I followed the information in this thread and it worked great!

one question, how do you force the emulator to open full screen?

when I run the launcher it never opens full screen, I know there must be a way, just have not found it.

---

### Post by capescw on 2008-09-19
Hi! Just joined group, after SUCCESSFULLY installing iseriesAccess on the 1st try, THANK YOU to n8bounds. However, one problem I can't find an answer to, perhaps you can assist. Emulator connecting to AS400, simple 'fill in the form' application. If I inadvertantly enter a numeric character in a field that is programmed to accept ONLY 1 of 5 alpha characters, I immediately get a 'lock-up', what appears to be a double cursor (_ + -), and a circular symbol (the actual cursor ?). No key sequence seems to clear the condition, I have to use pulldown 'Options - Reset'. IMPORTANT - these same AS400 programs work fine on 'iSeriesAccess' for Windows, allowing the user to backspace and enter the correct info. Obviously, any help would be greatly appreciated.

---

### Post by scottlpatterson on 2008-10-06
This works on Ubuntu 8.04! Here's what I did...

1. wget [http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb](http://ngbnet.homelinux.com/repository/unrestricted/linux/ibm5250/iseriesaccess_5.4.0-2.4_i386.deb)
2. sudo dpkg -i iseriesaccess_5.4.0-2.4_i386.deb
3. sudo apt-get install -f
4. sudo apt-get install msttcorefonts
5. sudo fc-cache -f -v
6. Create icon for AS400 (/opt/ibm/iSeriesAccess/bin/ibm5250 $SERVER)
[LIST]*replace $SERVER with a hostname or IP address*[/LIST]

---

### Post by jpaul6160 on 2009-03-13
It looks like the above deb download site has been shutdown.  I have not yet gotten either the v5r4 or the v6r1 installed on unbuntu 8.10 64 bit.

---

### Post by n8bounds on 2010-07-19
I'm back! I'm trying to get this working in Lucid, but can't.

Here's the fixed link! [http://n8.thruhere.net/export/free/ibm5250/](http://n8.thruhere.net/export/free/ibm5250/)

---

### Post by n8bounds on 2010-07-19
> **n8bounds said:**
> I'm back! I'm trying to get this working in Lucid, but can't.

Here's the fixed link! [http://n8.thruhere.net/export/free/ibm5250/](http://n8.thruhere.net/export/free/ibm5250/)

I figured it out! [http://n8.thruhere.net/blog/?p=142](http://n8.thruhere.net/blog/?p=142)

I updated the OP as well

---

### Post by warped6 on 2010-10-22
So I've been slowly upgrading all my various machines to 10.10 from 10.04.

First was my desktop, from 10.04 (64 bit) --> 10.10 (64 bit). Not a hitch and most importantly Iseries Access still worked.

On to other laptops. No problem.

Finally my main laptop 10.04 (32 bit) --> 10.10 (32 bit). Small hiccup, ok got over that. Iseries Access? BROKEN! Dang it. I go to reinstall and it complains about needing "odbcinst1debian1". Can't install that because it was superseded by odbcinst1debian2. Do I need to go back to the RPM and start from there? Redo the alien part?

Any help would be great.
Mike

---

### Post by warped6 on 2010-10-22
In answer to my own post... yes.

Downloaded iSeriesAccess 7.1 and went through redoing the alien and build package part to get the .deb file. Then went and just double click and installed it.

---

### Post by n8bounds on 2010-11-08
[IMG]http://s3.amazonaws.com/files.posterous.com/temp-2010-11-08/ruyxDBaodiwentJBqgljlknAurwFtyypqDHGdsqGfjppHsjsHAjGgxoFBpfF/ibm5250.png.scaled1000.png?AWSAccessKeyId=1C9REJR1EMRZ83Q7QRG2&Expires=1289230378&Signature=cXW84SXKy8/sG0Z4YBdBRaWjAQE%3D[/IMG]

Works for me...

---

### Post by egzz on 2011-03-30
Thx to the guy that published the script... Great Job!!!

Completely new to ubuntu.

I've an issue, I tried to install the latest version of iseries (7.1), it installed perfectly, but when I try to log in into the remote server, it says that the address could not be resolved. I'm using UBUNTU 8.04 LTS. Does anyone recommend to use the 5.4 version rather than 7.1?

Best regards!
Enrique.

---

### Post by n8bounds on 2011-05-10
Updated for Natty: [http://n8.thruhere.net/blog/?p=1122]("http://n8.thruhere.net/blog/?p=1122")

---

### Post by mozart_ar on 2011-05-10
> **n8bounds said:**
> Updated for Natty: [http://n8.thruhere.net/blog/?p=1122]("http://n8.thruhere.net/blog/?p=1122")

Thanks!

---

### Post by mozart_ar on 2011-08-23
n8bounds: I am seeing your blog down now, but I found this > [http://sourceforge.net/projects/ibm5250onubuntu/](http://sourceforge.net/projects/ibm5250onubuntu/) 

Is this sf project your?

---

### Post by RAPIDSTORM on 2011-10-25
Thnx Guys For the great topic,

after i did all of that and while i start ibm5250 i faced with this error

 ```

5250: [ INFORMATIONAL ]: Build Date: March 2008 (V6R1 1.0).
5250: [ ERROR ]: 

    ***** There are no fixed or scalable fonts unavailable                           *****
    ***** Session not starting. Please verify that the 75 and 100 DPI            *****
    ***** fixed fonts are installed..                                                            *****
    ***** The xlsfonts -fn "*-*-medium-r-normal--*-*-*-*-m-*" command    *****
    ***** will list the available fonts.                                                          *****


```

any help to solve it?

---

### Post by s_s_525 on 2011-10-25
dear all thanks for helping me to install  
but i tired to install iseries client access emulator :confused:

i download ( iseries access 6.1.0 i386.deb ) on Ubuntu 11.10 32bit [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

but i can't install it  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]
please can you help me [IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG]

Thanks and best regards:KS

---

### Post by amdemas on 2011-10-30
Hi, I keep getting this error.

```
ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: Error 40

```

I installed libmotif3 doing:

```
sudo dpkg -i --force-architecture libmotif3_2.2.3-2_i386.deb
```

I am running 11.10 x64 

Any suggestions?

---

### Post by amdemas on 2011-10-30
> **amdemas said:**
> Hi, I keep getting this error.

```
ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: Error 40

```

I installed libmotif3 doing:

```
sudo dpkg -i --force-architecture libmotif3_2.2.3-2_i386.deb
```

I am running 11.10 x64 

Any suggestions?

After doing:

```
sudo ln -s /usr/lib/libXm.so.4 /usr/lib/libXm.so.3

```

and

```
sudo ln -s /usr/lib32/libXm.so.4 /usr/lib32/libXm.so.3
```

I know get this error:

```
ibm5250: error while loading shared libraries: libXm.so.3: wrong ELF class: ELFCLASS64

```

I wonder if I am moving in the right direction and have just symlinked them incorrectly?

---

### Post by Ghost0100 on 2012-02-15
I have followed the directions completely.  Linking the libXm.so.3 with LibXm.so.4 does not work.  Below is the error, *nix version, and the version of iSeries Access that I am using.  Any help would be appreciated.


$ ibm5250
ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory


Linux 2.6.32-5-amd64 #1 SMP Mon Jan 16 16:22:28 UTC 2012 x86_64 GNU/Linux

iseriesaccess_7.1.0-2_i386.deb


--from:  Ghost0100

---

### Post by n8bounds on 2012-02-15
Here, start over: 

[http://sourceforge.net/projects/ibm5250onubuntu/](http://sourceforge.net/projects/ibm5250onubuntu/)

Try that script and tell me if it works afterwards.

I *just* used it yesterday to install ibm5250 V7R1 1.0 on Linux Mint 12 64bit.

---

### Post by Ghost0100 on 2012-02-15
Thanks, n8bounds.  I will give it a try.

---

### Post by Ghost0100 on 2012-02-15
Ok. Install seemed ok after executing script.  Ran ibm5250.  Errors. So I re-booted and this is where I am at:

$ ibm5250 170.xxx.xxx.xxx -title newdisplay -DISPLAY_NAME "xxx" 


5250: [ INFORMATIONAL ]: Build Date: September 2010 (V7R1 1.0).
5250: [ DEBUG ]: RegistryInfo::WhichKeyboard(): Could not open file /etc/X11/XF86Config or /etc/X11/xorg.conf.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ ERROR ]: NSC0017: Xt Warning: Missing charsets in String to FontSet conversion.
5250: [ DEBUG ]: RegistryInfo::WhichKeyboard(): Could not open file /etc/X11/XF86Config or /etc/X11/xorg.conf.
5250: [ DEBUG ]: RegistryInfo::WhichKeyboard(): Could not open file /etc/X11/XF86Config or /etc/X11/xorg.conf.
5250: [ DEBUG ]: RegistryInfo::WhichKeyboard(): Could not open file /etc/X11/XF86Config or /etc/X11/xorg.conf.
Segmentation fault


Any ideas?  Thanks!

---

### Post by n8bounds on 2012-02-15
> **n8bounds said:**
> Here, start over: 

[http://sourceforge.net/projects/ibm5250onubuntu/](http://sourceforge.net/projects/ibm5250onubuntu/)

Try that script and tell me if it works afterwards.

I *just* used it yesterday to install ibm5250 V7R1 1.0 on Linux Mint 12 64bit.

I know this sounds stupid and Windows-y, but reboot the machine and try running
```
  ibm5250 
```
again from a terminal.

---

### Post by Ghost0100 on 2012-02-16
> **n8bounds said:**
> I know this sounds stupid and Windows-y, but reboot the machine and try running
```
  ibm5250 
```
again from a terminal.

I powered down and back on.  No joy.  I un-installed and re-installed.  Here is the output:


Linux:~$ ./installIBM5250.sh iSeriesAccess-7.1.0-1.0.i386.rpm

Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for libmotif3 
No candidate version found for libmotif3
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         

--2012-02-15 17:11:30--  [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu4_i386.deb)
Resolving mirrors.kernel.org... 149.20.4.71
Connecting to mirrors.kernel.org|149.20.4.71|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 296190 (289K) [text/plain]
Saving to: “libstdc++5_3.3.6-15ubuntu4_i386.deb”

100%[===================================>] 296,190      509K/s   in 0.6s    

2012-02-15 17:11:31 (509 KB/s) - “libstdc++5_3.3.6-15ubuntu4_i386.deb” saved [296190/296190]

--2012-02-15 17:11:31--  [http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb)
Resolving mirrors.kernel.org... 149.20.4.71
Connecting to mirrors.kernel.org|149.20.4.71|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1282660 (1.2M) [text/plain]
Saving to: “libmotif3_2.2.3-2_i386.deb”

100%[===================================>] 1,282,660    671K/s   in 1.9s    

2012-02-15 17:11:33 (671 KB/s) - “libmotif3_2.2.3-2_i386.deb” saved [1282660/1282660]

x - debian-binary
x - control.tar.gz
x - data.tar.gz
x - debian-binary
x - control.tar.gz
x - data.tar.gz
Directories iSeriesAccess-7.1.0 and iSeriesAccess-7.1.0.orig prepared.
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: source package iseriesaccess
dpkg-buildpackage: source version 7.1.0-2
dpkg-buildpackage: source changed by David Bobson <david@David-Linux>
dpkg-architecture: warning: Specified GNU system type i486-linux-gnu does not match gcc system type x86_64-linux-gnu.
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build iSeriesAccess-7.1.0
 debian/rules clean
dh_testdir
dh_testroot
dh_clean -d
dh_clean: Compatibility levels before 5 are deprecated.
 debian/rules build
dh_testdir
 debian/rules binary
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: dh_clean -k is deprecated; use dh_prep instead
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/iseriesaccess
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: warning: couldn't find library libcwbcore.so needed by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbtrc (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libcwbcore.so needed by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbping (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libcwbcore.so needed by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbnltbl (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: warning: couldn't find library libcwbcore.so needed by debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbrc.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dpkg-shlibdeps: error: no dependency information found for /usr/lib32/libXm.so.3 (used by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/colormapper).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/iseriesaccess.substvars debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/keymapper debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbcopwr debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/playedit debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/rmtcmd debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/keypad debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/miscpref5250 debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbtrc debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/ibm5250 debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/rmtodbc debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/setup5250 debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/colormapper debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwblmsrv debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/helpviewer debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbping debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbrunsql debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/printapp debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbnltbl debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbodbcs.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbodbc.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbxda.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbcore.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbrc.so returned exit code 2
make: [binary-arch] Error 9 (ignored)
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: warning: Depends field of package iseriesaccess: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_md5sums: Compatibility levels before 5 are deprecated.
dh_builddeb
dh_builddeb: Compatibility levels before 5 are deprecated.
dpkg-deb: building package `iseriesaccess' in `../iseriesaccess_7.1.0-2_i386.deb'.
 dpkg-genchanges -b >../iseriesaccess_7.1.0-2_i386.changes
dpkg-genchanges: binary-only upload - not including any source code
 dpkg-source --after-build iSeriesAccess-7.1.0
dpkg-buildpackage: binary only upload (no source included)
Generating locales (this might take a while)...
  en_US.UTF-8... done
Generation complete.
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package iseriesaccess.
(Reading database ... 116076 files and directories currently installed.)
Unpacking iseriesaccess (from iseriesaccess_7.1.0-2_i386.deb) ...
Setting up iseriesaccess (7.1.0-2) ...
post install processing for iSeriesAccess 1.0...configure
iSeries Access ODBC Driver has been deleted (if it existed at all) because its usage count became zero
odbcinst: Driver installed. Usage count increased to 1. 
    Target directory is /etc
Locale en_US not found ( using locale -a ) this may cause the IBM 5250 emulator to fail.
Generating the locale en_US using locale-gen utility.
Generating locales (this might take a while)...
  en_US.UTF-8... done
Generation complete.

Script complete! You may need to restart your computer before this will work...

Launch the program like this:
ibm5250 192.168.156.whatever -title MyFancyTitleBar -DISPLAY_NAME "UBUNTUA UBUNTUB UBUNTUC UBUNTUD" -LANGID en_US

Uninstall the program like this:
sudo dpkg --remove iseriesaccess

---

### Post by n8bounds on 2012-02-16
Here's my machine with a fresh install of Ubuntu 64bit, downloading the script and the rpm and installing it:

```


kaixubuntu@xubuntu:~$ which ibm5250
kaixubuntu@xubuntu:~$ ibm5250
ibm5250: command not found
kaixubuntu@xubuntu:~$ lsb_release -a; uname -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
Linux xubuntu 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
kaixubuntu@xubuntu:~$ wget http://downloads.sourceforge.net/project/ibm5250onubuntu/installIBM5250.sh
--2012-02-16 16:05:09--  http://downloads.sourceforge.net/project/ibm5250onubuntu/installIBM5250.sh
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/ibm5250onubuntu/installIBM5250.sh [following]
--2012-02-16 16:05:11--  http://iweb.dl.sourceforge.net/project/ibm5250onubuntu/installIBM5250.sh
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2581 (2.5K) [text/x-sh]
Saving to: `installIBM5250.sh'

100%[============================================================================================>] 2,581       --.-K/s   in 0s      

2012-02-16 16:05:11 (19.6 MB/s) - `installIBM5250.sh' saved [2581/2581]

kaixubuntu@xubuntu:~$ wget http://downloads.sourceforge.net/project/ibm5250onubuntu/rpms/iSeriesAccess-7.1.0-1.0.i386.rpm
--2012-02-16 16:06:02--  http://downloads.sourceforge.net/project/ibm5250onubuntu/rpms/iSeriesAccess-7.1.0-1.0.i386.rpm
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-dca2.dl.sourceforge.net/project/ibm5250onubuntu/rpms/iSeriesAccess-7.1.0-1.0.i386.rpm [following]
--2012-02-16 16:06:02--  http://superb-dca2.dl.sourceforge.net/project/ibm5250onubuntu/rpms/iSeriesAccess-7.1.0-1.0.i386.rpm
Resolving superb-dca2.dl.sourceforge.net... 209.61.193.20
Connecting to superb-dca2.dl.sourceforge.net|209.61.193.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3780019 (3.6M) [application/octet-stream]
Saving to: `iSeriesAccess-7.1.0-1.0.i386.rpm'

100%[============================================================================================>] 3,780,019    903K/s   in 4.9s    

2012-02-16 16:06:08 (752 KB/s) - `iSeriesAccess-7.1.0-1.0.i386.rpm' saved [3780019/3780019]

kaixubuntu@xubuntu:~$ bash ./installIBM5250.sh ./iSeriesAccess-7.1.0-1.0.i386.rpm 

[sudo] password for kaixubuntu: 
Sorry, try again.
[sudo] password for kaixubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for libmotif3 
Note: selecting "ttf-mscorefonts-installer" instead of the
      virtual package "msttcorefonts"
No candidate version found for libmotif3
The following NEW packages will be installed:
  alien build-essential{a} cabextract{a} debhelper{a} dpkg-dev{a} fakeroot{a} g++{a} g++-4.6{a} gcc-4.6-base{a} gettext{a} 
  html2text{a} ia32-libs ia32-libs-multiarch{a} intltool-debian{a} lib32asound2{a} lib32bz2-1.0{a} lib32ffi6{a} lib32gcc1{a} 
  lib32ncurses5{a} lib32ncursesw5{a} lib32stdc++6{a} lib32tinfo5{a} lib32z1{a} libacl1{a} libalgorithm-diff-perl{a} 
  libalgorithm-diff-xs-perl{a} libalgorithm-merge-perl{a} libattr1{a} libaudio2{a} libavahi-client3{a} libavahi-common-data{a} 
  libavahi-common3{a} libc6{a} libc6-i386{a} libcomerr2{a} libcups2{a} libcupsimage2{a} libcurl3{a} libdb5.1{a} libdbus-1-3{a} 
  libdpkg-perl{a} libdrm-intel1{a} libdrm-nouveau1a{a} libdrm-radeon1{a} libdrm2{a} libexpat1{a} libffi6{a} libfontconfig1{a} 
  libfreetype6{a} libgcc1{a} libgcrypt11{a} libgdbm3{a} libgl1-mesa-dri{a} libgl1-mesa-glx{a} libglapi-mesa{a} libglib2.0-0{a} 
  libglib2.0-data{a} libgnutls26{a} libgpg-error0{a} libgssapi-krb5-2{a} libice6{a} libidn11{a} libjpeg62{a} libk5crypto3{a} 
  libkeyutils1{a} libkrb5-3{a} libkrb5support0{a} liblcms1{a} libldap-2.4-2{a} libllvm2.9{a} libmail-sendmail-perl{a} libmng1{a} 
  libmysqlclient16{ab} libnspr4{a} libnss3{a} libpciaccess0{a} libpcre3{a} libpng12-0{a} libqt4-dbus{a} libqt4-declarative{a} 
  libqt4-designer{a} libqt4-network{a} libqt4-opengl{a} libqt4-qt3support{a} libqt4-script{a} libqt4-scripttools{a} libqt4-sql{a} 
  libqt4-sql-mysql{a} libqt4-svg{a} libqt4-test{a} libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtgui4{a} librpm2{a} 
  librpmbuild2{a} librpmio2{a} librpmsign0{a} librtmp0{a} libsasl2-2{a} libsasl2-modules{a} libselinux1{a} libsm6{a} 
  libsqlite3-0{a} libssl1.0.0{a} libstdc++6{a} libstdc++6-4.6-dev{a} libsys-hostname-long-perl{a} libtasn1-3{a} libtiff4{a} 
  libunistring0{a} libuuid1{a} libx11-6{a} libxau6{a} libxcb1{a} libxdamage1{a} libxdmcp6{a} libxext6{a} libxfixes3{a} libxi6{a} 
  libxrender1{a} libxss1{a} libxt6{a} libxxf86vm1{a} odbcinst{a} odbcinst1debian2{a} patch{a} po-debconf{a} qdbus{a} rpm{a} 
  rpm-common{a} rpm2cpio{a} ttf-mscorefonts-installer unixodbc xfonts-100dpi xfonts-75dpi zlib1g{a} 
0 packages upgraded, 137 newly installed, 0 to remove and 0 not upgraded.
Need to get 96.9 MB of archives. After unpacking 316 MB will be used.
The following packages have unmet dependencies:
  libmysqlclient16: Depends: mysql-common (>= 5.1.58-1ubuntu1) which is a virtual package.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      ia32-libs-multiarch [Not Installed]                
2)      libacl1 [Not Installed]                            
3)      libattr1 [Not Installed]                           
4)      libaudio2 [Not Installed]                          
5)      libavahi-client3 [Not Installed]                   
6)      libavahi-common3 [Not Installed]                   
7)      libc6 [Not Installed]                              
8)      libcomerr2 [Not Installed]                         
9)      libcups2 [Not Installed]                           
10)     libcupsimage2 [Not Installed]                      
11)     libcurl3 [Not Installed]                           
12)     libdb5.1 [Not Installed]                           
13)     libdbus-1-3 [Not Installed]                        
14)     libdrm-intel1 [Not Installed]                      
15)     libdrm-nouveau1a [Not Installed]                   
16)     libdrm-radeon1 [Not Installed]                     
17)     libdrm2 [Not Installed]                            
18)     libexpat1 [Not Installed]                          
19)     libffi6 [Not Installed]                            
20)     libfontconfig1 [Not Installed]                     
21)     libfreetype6 [Not Installed]                       
22)     libgcc1 [Not Installed]                            
23)     libgcrypt11 [Not Installed]                        
24)     libgdbm3 [Not Installed]                           
25)     libgl1-mesa-dri [Not Installed]                    
26)     libgl1-mesa-glx [Not Installed]                    
27)     libglapi-mesa [Not Installed]                      
28)     libglib2.0-0 [Not Installed]                       
29)     libgnutls26 [Not Installed]                        
30)     libgpg-error0 [Not Installed]                      
31)     libgssapi-krb5-2 [Not Installed]                   
32)     libice6 [Not Installed]                            
33)     libidn11 [Not Installed]                           
34)     libjpeg62 [Not Installed]                          
35)     libk5crypto3 [Not Installed]                       
36)     libkeyutils1 [Not Installed]                       
37)     libkrb5-3 [Not Installed]                          
38)     libkrb5support0 [Not Installed]                    
39)     liblcms1 [Not Installed]                           
40)     libldap-2.4-2 [Not Installed]                      
41)     libllvm2.9 [Not Installed]                         
42)     libmng1 [Not Installed]                            
43)     libmysqlclient16 [Not Installed]                   
44)     libnspr4 [Not Installed]                           
45)     libnss3 [Not Installed]                            
46)     libpciaccess0 [Not Installed]                      
47)     libpcre3 [Not Installed]                           
48)     libpng12-0 [Not Installed]                         
49)     libqt4-dbus [Not Installed]                        
50)     libqt4-declarative [Not Installed]                 
51)     libqt4-designer [Not Installed]                    
52)     libqt4-network [Not Installed]                     
53)     libqt4-opengl [Not Installed]                      
54)     libqt4-qt3support [Not Installed]                  
55)     libqt4-script [Not Installed]                      
56)     libqt4-scripttools [Not Installed]                 
57)     libqt4-sql [Not Installed]                         
58)     libqt4-sql-mysql [Not Installed]                   
59)     libqt4-svg [Not Installed]                         
60)     libqt4-test [Not Installed]                        
61)     libqt4-xml [Not Installed]                         
62)     libqt4-xmlpatterns [Not Installed]                 
63)     libqtcore4 [Not Installed]                         
64)     libqtgui4 [Not Installed]                          
65)     librtmp0 [Not Installed]                           
66)     libsasl2-2 [Not Installed]                         
67)     libsasl2-modules [Not Installed]                   
68)     libselinux1 [Not Installed]                        
69)     libsm6 [Not Installed]                             
70)     libsqlite3-0 [Not Installed]                       
71)     libssl1.0.0 [Not Installed]                        
72)     libstdc++6 [Not Installed]                         
73)     libtasn1-3 [Not Installed]                         
74)     libtiff4 [Not Installed]                           
75)     libuuid1 [Not Installed]                           
76)     libx11-6 [Not Installed]                           
77)     libxau6 [Not Installed]                            
78)     libxcb1 [Not Installed]                            
79)     libxdamage1 [Not Installed]                        
80)     libxdmcp6 [Not Installed]                          
81)     libxext6 [Not Installed]                           
82)     libxfixes3 [Not Installed]                         
83)     libxi6 [Not Installed]                             
84)     libxrender1 [Not Installed]                        
85)     libxss1 [Not Installed]                            
86)     libxt6 [Not Installed]                             
87)     libxxf86vm1 [Not Installed]                        
88)     qdbus [Not Installed]                              
89)     zlib1g [Not Installed]                             

      Leave the following dependencies unresolved:         
90)     ia32-libs recommends ia32-libs-multiarch           
91)     ia32-libs-multiarch recommends libgl1-mesa-glx     
92)     ia32-libs-multiarch recommends libgl1-mesa-dri     
93)     libqtgui4 recommends libcups2                      


The following NEW packages will be installed:
  alien build-essential{a} cabextract{a} debhelper{a} dpkg-dev{a} fakeroot{a} g++{a} g++-4.6{a} gettext{a} html2text{a} ia32-libs 
  intltool-debian{a} lib32asound2{a} lib32bz2-1.0{a} lib32ffi6{a} lib32gcc1{a} lib32ncurses5{a} lib32ncursesw5{a} lib32stdc++6{a} 
  lib32tinfo5{a} lib32z1{a} libalgorithm-diff-perl{a} libalgorithm-diff-xs-perl{a} libalgorithm-merge-perl{a} libc6-i386{a} 
  libdpkg-perl{a} libglib2.0-data{a} libmail-sendmail-perl{a} librpm2{a} librpmbuild2{a} librpmio2{a} librpmsign0{a} 
  libstdc++6-4.6-dev{a} libsys-hostname-long-perl{a} libunistring0{a} odbcinst{a} odbcinst1debian2{a} patch{a} po-debconf{a} 
  rpm{a} rpm-common{a} rpm2cpio{a} ttf-mscorefonts-installer unixodbc xfonts-100dpi xfonts-75dpi 
The following packages are RECOMMENDED but will NOT be installed:
  ia32-libs-multiarch 
0 packages upgraded, 46 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.8 MB of archives. After unpacking 186 MB will be used.
Get: 1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libc6-i386 amd64 2.13-20ubuntu5 [3,851 kB]
Get: 2 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32gcc1 amd64 1:4.6.1-9ubuntu3 [54.1 kB]                                   
Get: 3 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32z1 amd64 1:1.2.3.4.dfsg-3ubuntu3 [49.4 kB]                              
Get: 4 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32stdc++6 amd64 4.6.1-9ubuntu3 [340 kB]                                   
Get: 5 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32asound2 amd64 1.0.24.1-0ubuntu10 [392 kB]                               
Get: 6 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main lib32bz2-1.0 amd64 1.0.5-6ubuntu1.11.10.1 [33.2 kB]                  
Get: 7 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32tinfo5 amd64 5.9-1ubuntu5 [63.2 kB]                                     
Get: 8 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32ncurses5 amd64 5.9-1ubuntu5 [139 kB]                                    
Get: 9 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32ffi6 amd64 3.0.11~rc1-2 [16.4 kB]                                       
Get: 10 http://us.archive.ubuntu.com/ubuntu/ oneiric/main lib32ncursesw5 amd64 5.9-1ubuntu5 [169 kB]                                  
Get: 11 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe ia32-libs amd64 20090808ubuntu26 [30.1 MB]                              
Get: 12 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5 [171 kB]                                   
Get: 13 http://us.archive.ubuntu.com/ubuntu/ oneiric/main patch amd64 2.6.1-2 [80.7 kB]                                               
Get: 14 http://us.archive.ubuntu.com/ubuntu/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5 [473 kB]                                       
Get: 15 http://us.archive.ubuntu.com/ubuntu/ oneiric/main html2text amd64 1.3.2a-15 [104 kB]                                          
Get: 16 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libunistring0 amd64 0.9.3-4 [426 kB]                                        
Get: 17 http://us.archive.ubuntu.com/ubuntu/ oneiric/main gettext amd64 0.18.1.1-3ubuntu1 [1,329 kB]                                  
Get: 18 http://us.archive.ubuntu.com/ubuntu/ oneiric/main intltool-debian all 0.35.0+20060710.1 [31.6 kB]                             
Get: 19 http://us.archive.ubuntu.com/ubuntu/ oneiric/main po-debconf all 1.0.16+nmu1 [212 kB]                                         
Get: 20 http://us.archive.ubuntu.com/ubuntu/ oneiric/main debhelper all 8.9.0ubuntu1 [487 kB]                                         
Get: 21 http://us.archive.ubuntu.com/ubuntu/ oneiric/main librpmio2 amd64 4.9.0-7 [81.6 kB]                                           
Get: 22 http://us.archive.ubuntu.com/ubuntu/ oneiric/main rpm-common amd64 4.9.0-7 [20.0 kB]                                          
Get: 23 http://us.archive.ubuntu.com/ubuntu/ oneiric/main librpm2 amd64 4.9.0-7 [185 kB]                                              
Get: 24 http://us.archive.ubuntu.com/ubuntu/ oneiric/main librpmbuild2 amd64 4.9.0-7 [68.9 kB]                                        
Get: 25 http://us.archive.ubuntu.com/ubuntu/ oneiric/main librpmsign0 amd64 4.9.0-7 [8,784 B]                                         
Get: 26 http://us.archive.ubuntu.com/ubuntu/ oneiric/main rpm2cpio amd64 4.9.0-7 [6,526 B]                                            
Get: 27 http://us.archive.ubuntu.com/ubuntu/ oneiric/main rpm amd64 4.9.0-7 [156 kB]                                                  
Get: 28 http://us.archive.ubuntu.com/ubuntu/ oneiric/main alien all 8.85 [58.6 kB]                                                    
Get: 29 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libstdc++6-4.6-dev amd64 4.6.1-9ubuntu3 [1,644 kB]                          
Get: 30 http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6 amd64 4.6.1-9ubuntu3 [6,970 kB]                                     
Get: 31 http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++ amd64 4:4.6.1-2ubuntu5 [1,444 B]                                        
Get: 32 http://us.archive.ubuntu.com/ubuntu/ oneiric/main build-essential amd64 11.5ubuntu1 [5,928 B]
Get: 33 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe cabextract amd64 1.4-1 [42.2 kB]                                        
Get: 34 http://us.archive.ubuntu.com/ubuntu/ oneiric/main fakeroot amd64 1.17-1 [107 kB]                                              
Get: 35 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]                              
Get: 36 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-xs-perl amd64 0.04-1build1 [13.4 kB]                      
Get: 37 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]                                
Get: 38 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libglib2.0-data amd64 2.30.0-0ubuntu4 [77.4 kB]                             
Get: 39 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libsys-hostname-long-perl all 1.4-2 [11.4 kB]                               
Get: 40 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libmail-sendmail-perl all 0.79.16-1 [26.5 kB]                               
Get: 41 http://us.archive.ubuntu.com/ubuntu/ oneiric/main odbcinst1debian2 amd64 2.2.14p2-2ubuntu1 [52.1 kB]                          
Get: 42 http://us.archive.ubuntu.com/ubuntu/ oneiric/main odbcinst amd64 2.2.14p2-2ubuntu1 [13.3 kB]                                  
Get: 43 http://us.archive.ubuntu.com/ubuntu/ oneiric/multiverse ttf-mscorefonts-installer all 3.3ubuntu4 [34.8 kB]                    
Get: 44 http://us.archive.ubuntu.com/ubuntu/ oneiric/main unixodbc amd64 2.2.14p2-2ubuntu1 [244 kB]                                   
Get: 45 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xfonts-100dpi all 1:1.0.3 [3,908 kB]                                    
Get: 46 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe xfonts-75dpi all 1:1.0.3 [3,464 kB]                                     
Fetched 55.8 MB in 1min 6s (835 kB/s)                                                                                                 
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package libc6-i386.
(Reading database ... 157829 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.13-20ubuntu5_amd64.deb) ...
Selecting previously deselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package lib32z1.
Unpacking lib32z1 (from .../lib32z1_1%3a1.2.3.4.dfsg-3ubuntu3_amd64.deb) ...
Selecting previously deselected package lib32stdc++6.
Unpacking lib32stdc++6 (from .../lib32stdc++6_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package lib32asound2.
Unpacking lib32asound2 (from .../lib32asound2_1.0.24.1-0ubuntu10_amd64.deb) ...
Setting up libc6-i386 (2.13-20ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package lib32bz2-1.0.
(Reading database ... 158150 files and directories currently installed.)
Unpacking lib32bz2-1.0 (from .../lib32bz2-1.0_1.0.5-6ubuntu1.11.10.1_amd64.deb) ...
Selecting previously deselected package lib32tinfo5.
Unpacking lib32tinfo5 (from .../lib32tinfo5_5.9-1ubuntu5_amd64.deb) ...
Selecting previously deselected package lib32ncurses5.
Unpacking lib32ncurses5 (from .../lib32ncurses5_5.9-1ubuntu5_amd64.deb) ...
Selecting previously deselected package lib32ffi6.
Unpacking lib32ffi6 (from .../lib32ffi6_3.0.11~rc1-2_amd64.deb) ...
Selecting previously deselected package lib32ncursesw5.
Unpacking lib32ncursesw5 (from .../lib32ncursesw5_5.9-1ubuntu5_amd64.deb) ...
Selecting previously deselected package ia32-libs.
Unpacking ia32-libs (from .../ia32-libs_20090808ubuntu26_amd64.deb) ...
Selecting previously deselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.0.3ubuntu5_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6.1-2_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.0.3ubuntu5_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-15_amd64.deb) ...
Selecting previously deselected package libunistring0.
Unpacking libunistring0 (from .../libunistring0_0.9.3-4_amd64.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.18.1.1-3ubuntu1_amd64.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.16+nmu1_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_8.9.0ubuntu1_all.deb) ...
Selecting previously deselected package librpmio2.
Unpacking librpmio2 (from .../librpmio2_4.9.0-7_amd64.deb) ...
Selecting previously deselected package rpm-common.
Unpacking rpm-common (from .../rpm-common_4.9.0-7_amd64.deb) ...
Selecting previously deselected package librpm2.
Unpacking librpm2 (from .../librpm2_4.9.0-7_amd64.deb) ...
Selecting previously deselected package librpmbuild2.
Unpacking librpmbuild2 (from .../librpmbuild2_4.9.0-7_amd64.deb) ...
Selecting previously deselected package librpmsign0.
Unpacking librpmsign0 (from .../librpmsign0_4.9.0-7_amd64.deb) ...
Selecting previously deselected package rpm2cpio.
Unpacking rpm2cpio (from .../rpm2cpio_4.9.0-7_amd64.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../archives/rpm_4.9.0-7_amd64.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../archives/alien_8.85_all.deb) ...
Selecting previously deselected package libstdc++6-4.6-dev.
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.1-9ubuntu3_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.1-2ubuntu5_amd64.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu1_amd64.deb) ...
Selecting previously deselected package cabextract.
Unpacking cabextract (from .../cabextract_1.4-1_amd64.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_amd64.deb) ...
Selecting previously deselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously deselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-1build1_amd64.deb) ...
Selecting previously deselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously deselected package libglib2.0-data.
Unpacking libglib2.0-data (from .../libglib2.0-data_2.30.0-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libsys-hostname-long-perl.
Unpacking libsys-hostname-long-perl (from .../libsys-hostname-long-perl_1.4-2_all.deb) ...
Selecting previously deselected package libmail-sendmail-perl.
Unpacking libmail-sendmail-perl (from .../libmail-sendmail-perl_0.79.16-1_all.deb) ...
Selecting previously deselected package odbcinst1debian2.
Unpacking odbcinst1debian2 (from .../odbcinst1debian2_2.2.14p2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package odbcinst.
Unpacking odbcinst (from .../odbcinst_2.2.14p2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package ttf-mscorefonts-installer.
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.3ubuntu4_all.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.14p2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package xfonts-100dpi.
Unpacking xfonts-100dpi (from .../xfonts-100dpi_1%3a1.0.3_all.deb) ...
Selecting previously deselected package xfonts-75dpi.
Unpacking xfonts-75dpi (from .../xfonts-75dpi_1%3a1.0.3_all.deb) ...
Processing triggers for libglib2.0-0 ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for fontconfig ...
Setting up lib32gcc1 (1:4.6.1-9ubuntu3) ...
Setting up lib32z1 (1:1.2.3.4.dfsg-3ubuntu3) ...
Setting up lib32stdc++6 (4.6.1-9ubuntu3) ...
Setting up lib32asound2 (1.0.24.1-0ubuntu10) ...
Setting up lib32bz2-1.0 (1.0.5-6ubuntu1.11.10.1) ...
Setting up lib32tinfo5 (5.9-1ubuntu5) ...
Setting up lib32ncurses5 (5.9-1ubuntu5) ...
Setting up lib32ffi6 (3.0.11~rc1-2) ...
Setting up lib32ncursesw5 (5.9-1ubuntu5) ...
Setting up ia32-libs (20090808ubuntu26) ...
Setting up libdpkg-perl (1.16.0.3ubuntu5) ...
Setting up patch (2.6.1-2) ...
Setting up dpkg-dev (1.16.0.3ubuntu5) ...
Setting up html2text (1.3.2a-15) ...
Setting up libunistring0 (0.9.3-4) ...
Setting up gettext (0.18.1.1-3ubuntu1) ...
Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.16+nmu1) ...
Setting up debhelper (8.9.0ubuntu1) ...
Setting up librpmio2 (4.9.0-7) ...
Setting up rpm-common (4.9.0-7) ...
Setting up librpm2 (4.9.0-7) ...
Setting up librpmbuild2 (4.9.0-7) ...
Setting up librpmsign0 (4.9.0-7) ...
Setting up rpm2cpio (4.9.0-7) ...
Setting up rpm (4.9.0-7) ...
Setting up alien (8.85) ...
Setting up cabextract (1.4-1) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-1build1) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libglib2.0-data (2.30.0-0ubuntu4) ...
Setting up libsys-hostname-long-perl (1.4-2) ...
Setting up libmail-sendmail-perl (0.79.16-1) ...
Setting up ttf-mscorefonts-installer (3.3ubuntu4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2012-02-16 16:08:03--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2012-02-16 16:08:03--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2012-02-16 16:08:04--  http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving superb-sea2.dl.sourceforge.net... 209.160.57.180
Connecting to superb-sea2.dl.sourceforge.net|209.160.57.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

     0K .......... .......... .......... .......... .......... 25%  147K 1s
    50K .......... .......... .......... .......... .......... 51%  490K 0s
   100K .......... .......... .......... .......... .......... 77%  572K 0s
   150K .......... .......... .......... .......... ...       100% 1.11M=0.6s

2012-02-16 16:08:08 (341 KB/s) - `./andale32.exe' saved [198384/198384]

--2012-02-16 16:08:08--  http://downloads.sourceforge.net/corefonts/arialb32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2012-02-16 16:08:09--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe [following]
--2012-02-16 16:08:09--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/octet-stream]
Saving to: `./arialb32.exe'

     0K .......... .......... .......... .......... .......... 30%  138K 1s
    50K .......... .......... .......... .......... .......... 60%  302K 0s
   100K .......... .......... .......... .......... .......... 91% 1.14M 0s
   150K .......... ....                                       100%  304K=0.6s

2012-02-16 16:08:10 (266 KB/s) - `./arialb32.exe' saved [168176/168176]

--2012-02-16 16:08:10--  http://downloads.sourceforge.net/corefonts/arial32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2012-02-16 16:08:10--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe [following]
--2012-02-16 16:08:10--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe
Resolving voxel.dl.sourceforge.net... 74.63.46.208, 74.63.46.221, 74.63.46.131, ...
Connecting to voxel.dl.sourceforge.net|74.63.46.208|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

     0K .......... .......... .......... .......... ..........  9%  547K 1s
    50K .......... .......... .......... .......... .......... 18% 1.12M 1s
   100K .......... .......... .......... .......... .......... 27% 1.10M 0s
   150K .......... .......... .......... .......... .......... 36% 1.12M 0s
   200K .......... .......... .......... .......... .......... 46% 1.09M 0s
   250K .......... .......... .......... .......... .......... 55% 1.14M 0s
   300K .......... .......... .......... .......... .......... 64% 1.12M 0s
   350K .......... .......... .......... .......... .......... 73% 1.08M 0s
   400K .......... .......... .......... .......... .......... 83% 1.13M 0s
   450K .......... .......... .......... .......... .......... 92% 1.12M 0s
   500K .......... .......... .......... .......... .         100% 1.08M=0.5s

2012-02-16 16:08:11 (1.01 MB/s) - `./arial32.exe' saved [554208/554208]

--2012-02-16 16:08:11--  http://downloads.sourceforge.net/corefonts/comic32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2012-02-16 16:08:11--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe [following]
--2012-02-16 16:08:11--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/x-msdos-program]
Saving to: `./comic32.exe'

     0K .......... .......... .......... .......... .......... 20%  359K 1s
    50K .......... .......... .......... .......... .......... 41%  820K 0s
   100K .......... .......... .......... .......... .......... 62% 1.08M 0s
   150K .......... .......... .......... .......... .......... 83% 1.12M 0s
   200K .......... .......... .......... ..........           100% 1.09M=0.3s

2012-02-16 16:08:12 (739 KB/s) - `./comic32.exe' saved [246008/246008]

--2012-02-16 16:08:12--  http://downloads.sourceforge.net/corefonts/courie32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2012-02-16 16:08:12--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe [following]
--2012-02-16 16:08:12--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/octet-stream]
Saving to: `./courie32.exe'

     0K .......... .......... .......... .......... ..........  7%  140K 4s
    50K .......... .......... .......... .......... .......... 15%  308K 3s
   100K .......... .......... .......... .......... .......... 23%  543K 2s
   150K .......... .......... .......... .......... .......... 31%  549K 2s
   200K .......... .......... .......... .......... .......... 39%  944K 1s
   250K .......... .......... .......... .......... .......... 47%  543K 1s
   300K .......... .......... .......... .......... .......... 55%  555K 1s
   350K .......... .......... .......... .......... .......... 63%  606K 1s
   400K .......... .......... .......... .......... .......... 71%  543K 0s
   450K .......... .......... .......... .......... .......... 79%  918K 0s
   500K .......... .......... .......... .......... .......... 87%  543K 0s
   550K .......... .......... .......... .......... .......... 95%  549K 0s
   600K .......... .......... .......... .                    100%  688K=1.4s

2012-02-16 16:08:14 (453 KB/s) - `./courie32.exe' saved [646368/646368]

--2012-02-16 16:08:14--  http://downloads.sourceforge.net/corefonts/georgi32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2012-02-16 16:08:14--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe [following]
--2012-02-16 16:08:14--  http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/x-msdos-program]
Saving to: `./georgi32.exe'

     0K .......... .......... .......... .......... .......... 13%  360K 1s
    50K .......... .......... .......... .......... .......... 26%  812K 1s
   100K .......... .......... .......... .......... .......... 39% 1.09M 0s
   150K .......... .......... .......... .......... .......... 52% 1.11M 0s
   200K .......... .......... .......... .......... .......... 65% 1.11M 0s
   250K .......... .......... .......... .......... .......... 78% 1.09M 0s
   300K .......... .......... .......... .......... .......... 91% 1.12M 0s
   350K .......... .......... .......... ...                  100% 1.09M=0.5s

2012-02-16 16:08:15 (849 KB/s) - `./georgi32.exe' saved [392440/392440]

--2012-02-16 16:08:15--  http://downloads.sourceforge.net/corefonts/impact32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following]
--2012-02-16 16:08:15--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe [following]
--2012-02-16 16:08:15--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `./impact32.exe'

     0K .......... .......... .......... .......... .......... 29%  144K 1s
    50K .......... .......... .......... .......... .......... 59%  321K 0s
   100K .......... .......... .......... .......... .......... 88% 1.02M 0s
   150K .......... .........                                  100%  487K=0.6s

2012-02-16 16:08:16 (287 KB/s) - `./impact32.exe' saved [173288/173288]

--2012-02-16 16:08:16--  http://downloads.sourceforge.net/corefonts/times32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following]
--2012-02-16 16:08:16--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe [following]
--2012-02-16 16:08:16--  http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe
Resolving superb-sea2.dl.sourceforge.net... 209.160.57.180
Connecting to superb-sea2.dl.sourceforge.net|209.160.57.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

     0K .......... .......... .......... .......... ..........  7%  149K 4s
    50K .......... .......... .......... .......... .......... 15%  408K 3s
   100K .......... .......... .......... .......... .......... 23%  553K 2s
   150K .......... .......... .......... .......... .......... 30%  224K 2s
   200K .......... .......... .......... .......... .......... 38% 1.13M 1s
   250K .......... .......... .......... .......... .......... 46%  775K 1s
   300K .......... .......... .......... .......... .......... 54% 1.08M 1s
   350K .......... .......... .......... .......... .......... 61%  197K 1s
   400K .......... .......... .......... .......... .......... 69% 1.10M 1s
   450K .......... .......... .......... .......... .......... 77% 1.12M 0s
   500K .......... .......... .......... .......... .......... 85% 1.12M 0s
   550K .......... .......... .......... .......... .......... 92% 1.09M 0s
   600K .......... .......... .......... .......... ......    100% 1.14M=1.4s

2012-02-16 16:08:18 (463 KB/s) - `./times32.exe' saved [661728/661728]

--2012-02-16 16:08:18--  http://downloads.sourceforge.net/corefonts/trebuc32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following]
--2012-02-16 16:08:19--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe [following]
--2012-02-16 16:08:19--  http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `./trebuc32.exe'

     0K .......... .......... .......... .......... .......... 14%  138K 2s
    50K .......... .......... .......... .......... .......... 28%  302K 1s
   100K .......... .......... .......... .......... .......... 43%  535K 1s
   150K .......... .......... .......... .......... .......... 57%  540K 1s
   200K .......... .......... .......... .......... .......... 71% 1.07M 0s
   250K .......... .......... .......... .......... .......... 86%  535K 0s
   300K .......... .......... .......... .......... ........  100%  555K=0.9s

2012-02-16 16:08:20 (371 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2012-02-16 16:08:20--  http://downloads.sourceforge.net/corefonts/verdan32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following]
--2012-02-16 16:08:20--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe [following]
--2012-02-16 16:08:20--  http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe
Resolving voxel.dl.sourceforge.net... 74.63.46.134, 74.63.46.208, 74.63.46.221, ...
Connecting to voxel.dl.sourceforge.net|74.63.46.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/octet-stream]
Saving to: `./verdan32.exe'

     0K .......... .......... .......... .......... .......... 14%  564K 1s
    50K .......... .......... .......... .......... .......... 29% 1.12M 0s
   100K .......... .......... .......... .......... .......... 43% 1.10M 0s
   150K .......... .......... .......... .......... .......... 58% 1.12M 0s
   200K .......... .......... .......... .......... .......... 72% 1.10M 0s
   250K .......... .......... .......... .......... .......... 87% 1.12M 0s
   300K .......... .......... .......... .......... ...       100% 1.13M=0.3s

2012-02-16 16:08:21 (994 KB/s) - `./verdan32.exe' saved [351992/351992]

--2012-02-16 16:08:21--  http://downloads.sourceforge.net/corefonts/webdin32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following]
--2012-02-16 16:08:21--  http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe [following]
--2012-02-16 16:08:21--  http://superb-sea2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe
Resolving superb-sea2.dl.sourceforge.net... 209.160.57.180
Connecting to superb-sea2.dl.sourceforge.net|209.160.57.180|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

     0K .......... .......... .......... .......... .......... 27%  141K 1s
    50K .......... .......... .......... .......... .......... 55%  236K 0s
   100K .......... .......... .......... .......... .......... 82%  410K 0s
   150K .......... .......... ..........                      100% 1.16M=0.7s

2012-02-16 16:08:25 (253 KB/s) - `./webdin32.exe' saved [185072/185072]

andale32.exe: OK
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: OK
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: OK
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: OK
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: OK
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
georgi32.exe: OK
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: OK
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
times32.exe: OK
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
trebuc32.exe: OK
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
verdan32.exe: OK
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
webdin32.exe: OK
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
Setting up xfonts-100dpi (1:1.0.3) ...
Setting up xfonts-75dpi (1:1.0.3) ...
Setting up libstdc++6-4.6-dev (4.6.1-9ubuntu3) ...
Setting up odbcinst (2.2.14p2-2ubuntu1) ...
Setting up odbcinst1debian2 (2.2.14p2-2ubuntu1) ...
Setting up unixodbc (2.2.14p2-2ubuntu1) ...
Setting up g++-4.6 (4.6.1-9ubuntu3) ...
Setting up g++ (4:4.6.1-2ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         

--2012-02-16 16:08:37--  http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-15ubuntu4_i386.deb
Resolving mirrors.kernel.org... 149.20.4.71
Connecting to mirrors.kernel.org|149.20.4.71|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 296190 (289K) [text/plain]
Saving to: `libstdc++5_3.3.6-15ubuntu4_i386.deb'

100%[============================================================================================>] 296,190      646K/s   in 0.4s    

2012-02-16 16:08:38 (646 KB/s) - `libstdc++5_3.3.6-15ubuntu4_i386.deb' saved [296190/296190]

--2012-02-16 16:08:38--  http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-2_i386.deb
Resolving mirrors.kernel.org... 149.20.4.71
Connecting to mirrors.kernel.org|149.20.4.71|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1282660 (1.2M) [text/plain]
Saving to: `libmotif3_2.2.3-2_i386.deb'

100%[============================================================================================>] 1,282,660    930K/s   in 1.3s    

2012-02-16 16:08:39 (930 KB/s) - `libmotif3_2.2.3-2_i386.deb' saved [1282660/1282660]

x - debian-binary
x - control.tar.gz
x - data.tar.gz
x - debian-binary
x - control.tar.gz
x - data.tar.gz
Directories iSeriesAccess-7.1.0 and iSeriesAccess-7.1.0.orig prepared.
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package iseriesaccess
dpkg-buildpackage: source version 7.1.0-2
dpkg-buildpackage: source changed by root <root@xubuntu>
dpkg-architecture: warning: Specified GNU system type i686-linux-gnu does not match gcc system type x86_64-linux-gnu.
dpkg-buildpackage: host architecture i386
 dpkg-source --before-build iSeriesAccess-7.1.0
 debian/rules clean
dh_testdir
dh_testroot
dh_clean -d
 debian/rules build
dh_testdir
 debian/rules binary
dh_testdir
dh_testdir
dh_testroot
dh_prep
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/iseriesaccess
dh_compress
dh_makeshlibs
Can't exec "i686-linux-gnu-objdump": No such file or directory at /usr/bin/dh_makeshlibs line 161, <FIND> line 1.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 162, <FIND> line 1.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 167, <FIND> line 1.
Can't exec "i686-linux-gnu-objdump": No such file or directory at /usr/bin/dh_makeshlibs line 161, <FIND> line 2.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 162, <FIND> line 2.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 167, <FIND> line 2.
Can't exec "i686-linux-gnu-objdump": No such file or directory at /usr/bin/dh_makeshlibs line 161, <FIND> line 3.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 162, <FIND> line 3.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 167, <FIND> line 3.
Can't exec "i686-linux-gnu-objdump": No such file or directory at /usr/bin/dh_makeshlibs line 161, <FIND> line 4.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 162, <FIND> line 4.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 167, <FIND> line 4.
Can't exec "i686-linux-gnu-objdump": No such file or directory at /usr/bin/dh_makeshlibs line 161, <FIND> line 5.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 162, <FIND> line 5.
Use of uninitialized value $ret in pattern match (m//) at /usr/bin/dh_makeshlibs line 167, <FIND> line 5.
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: couldn't find library libcwbcore.so needed by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbtrc (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libcwbcore.so needed by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbping (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: warning: couldn't find library libcwbcore.so needed by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbnltbl (ELF format: 'elf32-i386'; RPATH: '').
dpkg-shlibdeps: error: no dependency information found for /usr/lib32/libXm.so.3 (used by debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/colormapper).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/iseriesaccess.substvars debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbodbc.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbcore.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbodbcs.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbxda.so debian/iseriesaccess/opt/ibm/iSeriesAccess/lib/libcwbrc.so debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/ibm5250 debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbping debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/setup5250 debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbrunsql debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/playedit debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/printapp debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/miscpref5250 debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwblmsrv debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbtrc debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/helpviewer debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/keymapper debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbnltbl debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/keypad debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/rmtcmd debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/rmtodbc debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/cwbcopwr debian/iseriesaccess/opt/ibm/iSeriesAccess/bin/colormapper returned exit code 2
make: [binary-arch] Error 2 (ignored)
dh_gencontrol
dpkg-gencontrol: warning: Depends field of package iseriesaccess: unknown substitution variable ${shlibs:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: building package `iseriesaccess:i386' in `../iseriesaccess_7.1.0-2_i386.deb'.
 dpkg-genchanges -b >../iseriesaccess_7.1.0-2_i386.changes
dpkg-genchanges: binary-only upload - not including any source code
 dpkg-source --after-build iSeriesAccess-7.1.0
dpkg-buildpackage: binary only upload (no source included)
Generating locales...
  en_US.ISO-8859-1... done
Generation complete.
Selecting previously deselected package iseriesaccess:i386.
(Reading database ... 162292 files and directories currently installed.)
Unpacking iseriesaccess:i386 (from iseriesaccess_7.1.0-2_i386.deb) ...
Setting up iseriesaccess:i386 (7.1.0-2) ...
post install processing for iSeriesAccess 1.0...configure
iSeries Access ODBC Driver has been deleted (if it existed at all) because its usage count became zero
odbcinst: Driver installed. Usage count increased to 1. 
    Target directory is /etc
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

Script complete! You may need to restart your computer before this will work...

Launch the program like this:
ibm5250 192.168.156.whatever -title MyFancyTitleBar -DISPLAY_NAME "UBUNTUA UBUNTUB UBUNTUC UBUNTUD" -LANGID en_US

Uninstall the program like this:
sudo dpkg --remove iseriesaccess

kaixubuntu@xubuntu:~$ which ibm5250 ; ibm5250
/usr/bin/ibm5250
5250: [ INFORMATIONAL ]: Build Date: September 2010 (V7R1 1.0).
5250: [ DEBUG ]: RegistryInfo::WhichKeyboard(): Could not open file /etc/X11/XF86Config or /etc/X11/xorg.conf.
5250: [ ERROR ]: 

	***** There are no fixed or scalable fonts unavailable            *****
	***** Session not starting. Please verify that the 75 and 100 DPI *****
	***** fixed fonts are installed..                                 *****
	***** The xlsfonts -fn "*-*-medium-r-normal--*-*-*-*-m-*" command *****
	***** will list the available fonts.                              *****

Segmentation fault
kaixubuntu@xubuntu:~$ 


```

As you can see, it doesn't work just yet. Launching it the first time offers an authentication window, but then crashes. 

Reboot and then it works!

Here is the output of lsof against the ibm5250 pid:

```


kaixubuntu@xubuntu:~$ man lsof 
kaixubuntu@xubuntu:~$ ps aux^C
kaixubuntu@xubuntu:~$ clear 
kaixubuntu@xubuntu:~$ ps aux | grep ibm
1001      9380  0.0  0.0  15172  5608 pts/0    S+   16:14   0:00 ibm5250
1001      9453  0.0  0.0  13708   896 pts/1    S+   16:15   0:00 grep --color=auto ibm
kaixubuntu@xubuntu:~$ lsof -p 9380
COMMAND  PID       USER   FD   TYPE             DEVICE SIZE/OFF    NODE NAME
ibm5250 9380 kaixubuntu  cwd    DIR              253,0     4096 1835009 /home/kaixubuntu
ibm5250 9380 kaixubuntu  rtd    DIR               8,10     4096       2 /
ibm5250 9380 kaixubuntu  txt    REG               8,10  1662340  298748 /opt/ibm/iSeriesAccess/bin/ibm5250
ibm5250 9380 kaixubuntu  mem    REG               8,10    38356  176087 /usr/lib32/libXcursor.so.1.0.2
ibm5250 9380 kaixubuntu  mem    REG               8,10     9588  174639 /usr/lib32/gconv/ISO8859-1.so
ibm5250 9380 kaixubuntu  mem    REG               8,10    26050  154033 /usr/lib32/gconv/gconv-modules.cache
ibm5250 9380 kaixubuntu  mem    REG               8,10  7490080  266510 /usr/lib/locale/locale-archive
ibm5250 9380 kaixubuntu  mem    REG               8,10    21820  176091 /usr/lib32/libXdmcp.so.6.0.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    30684  138283 /lib32/librt-2.13.so
ibm5250 9380 kaixubuntu  mem    REG               8,10   124483  139609 /lib32/libpthread-2.13.so
ibm5250 9380 kaixubuntu  mem    REG               8,10   120332  176279 /usr/lib32/libxcb.so.1.1.0
ibm5250 9380 kaixubuntu  mem    REG               8,10     9588  176083 /usr/lib32/libXau.so.6.0.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    18008  175257 /lib32/libuuid.so.1.3.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    13940  139596 /lib32/libdl-2.13.so
ibm5250 9380 kaixubuntu  mem    REG               8,10  1532104  139592 /lib32/libc-2.13.so
ibm5250 9380 kaixubuntu  mem    REG               8,10   116232  174943 /usr/lib32/libgcc_s.so.1
ibm5250 9380 kaixubuntu  mem    REG               8,10   169476  139618 /lib32/libm-2.13.so
ibm5250 9380 kaixubuntu  mem    REG               8,10   930320  174991 /usr/lib32/libstdc++.so.6.0.16
ibm5250 9380 kaixubuntu  mem    REG               8,10  1288080  298702 /opt/ibm/iSeriesAccess/lib/libcwbcore.so
ibm5250 9380 kaixubuntu  mem    REG               8,10    63112  175897 /usr/lib32/libXpm.so.4.11.0
ibm5250 9380 kaixubuntu  mem    REG               8,10  1262456  176081 /usr/lib32/libX11.so.6.3.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    30432  175895 /usr/lib32/libXp.so.6.2.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    72328  176093 /usr/lib32/libXext.so.6.4.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    92364  176073 /usr/lib32/libICE.so.6.3.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    30108  176077 /usr/lib32/libSM.so.6.0.1
ibm5250 9380 kaixubuntu  mem    REG               8,10   372012  176107 /usr/lib32/libXt.so.6.0.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    96676  175893 /usr/lib32/libXmu.so.6.2.0
ibm5250 9380 kaixubuntu  mem    REG               8,10  2349356  174941 /usr/lib32/libXm.so.3.0.2
ibm5250 9380 kaixubuntu  mem    REG               8,10    17712  176095 /usr/lib32/libXfixes.so.3.1.0
ibm5250 9380 kaixubuntu  mem    REG               8,10    38520  176105 /usr/lib32/libXrender.so.1.3.0
ibm5250 9380 kaixubuntu  mem    REG               8,10   126152  139608 /lib32/ld-2.13.so
ibm5250 9380 kaixubuntu    0u   CHR              136,0      0t0       3 /dev/pts/0
ibm5250 9380 kaixubuntu    1u   CHR              136,0      0t0       3 /dev/pts/0
ibm5250 9380 kaixubuntu    2u   CHR              136,0      0t0       3 /dev/pts/0
ibm5250 9380 kaixubuntu    3u  unix 0x0000000000000000      0t0   32048 socket
ibm5250 9380 kaixubuntu    4u  unix 0x0000000000000000      0t0   32049 socket
kaixubuntu@xubuntu:~$ 

```

---

### Post by n8bounds on 2012-02-16
Proof: [http://i.imgur.com/HvHqC.png](http://i.imgur.com/HvHqC.png)

Here's lsof with a working, running window from the above referenced screenshot session:

```


kaixubuntu@xubuntu:~$ ps aux | grep ibm
1001      1994  0.2  0.0  16240  7368 pts/0    S+   16:21   0:00 ibm5250
1001      2053  0.0  0.0  13708   900 pts/1    S+   16:22   0:00 grep --color=auto ibm
kaixubuntu@xubuntu:~$ lsof -p 1994
COMMAND  PID       USER   FD   TYPE             DEVICE SIZE/OFF    NODE NAME
ibm5250 1994 kaixubuntu  cwd    DIR              253,0     4096 1835009 /home/kaixubuntu
ibm5250 1994 kaixubuntu  rtd    DIR               8,10     4096       2 /
ibm5250 1994 kaixubuntu  txt    REG               8,10  1662340  298748 /opt/ibm/iSeriesAccess/bin/ibm5250
ibm5250 1994 kaixubuntu  mem    REG               8,10    79712  139601 /lib32/libresolv-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10    46736  139598 /lib32/libnss_files-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10    38356  176087 /usr/lib32/libXcursor.so.1.0.2
ibm5250 1994 kaixubuntu  mem    REG               8,10    22092  139603 /lib32/libnss_dns-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10     9588  174639 /usr/lib32/gconv/ISO8859-1.so
ibm5250 1994 kaixubuntu  mem    REG               8,10    26050  154033 /usr/lib32/gconv/gconv-modules.cache
ibm5250 1994 kaixubuntu  mem    REG               8,10  7490080  266510 /usr/lib/locale/locale-archive
ibm5250 1994 kaixubuntu  mem    REG               8,10    21820  176091 /usr/lib32/libXdmcp.so.6.0.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    30684  138283 /lib32/librt-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10   124483  139609 /lib32/libpthread-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10   120332  176279 /usr/lib32/libxcb.so.1.1.0
ibm5250 1994 kaixubuntu  mem    REG               8,10     9588  176083 /usr/lib32/libXau.so.6.0.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    18008  175257 /lib32/libuuid.so.1.3.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    13940  139596 /lib32/libdl-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10  1532104  139592 /lib32/libc-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10   116232  174943 /usr/lib32/libgcc_s.so.1
ibm5250 1994 kaixubuntu  mem    REG               8,10   169476  139618 /lib32/libm-2.13.so
ibm5250 1994 kaixubuntu  mem    REG               8,10   930320  174991 /usr/lib32/libstdc++.so.6.0.16
ibm5250 1994 kaixubuntu  mem    REG               8,10  1288080  298702 /opt/ibm/iSeriesAccess/lib/libcwbcore.so
ibm5250 1994 kaixubuntu  mem    REG               8,10    63112  175897 /usr/lib32/libXpm.so.4.11.0
ibm5250 1994 kaixubuntu  mem    REG               8,10  1262456  176081 /usr/lib32/libX11.so.6.3.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    30432  175895 /usr/lib32/libXp.so.6.2.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    72328  176093 /usr/lib32/libXext.so.6.4.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    92364  176073 /usr/lib32/libICE.so.6.3.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    30108  176077 /usr/lib32/libSM.so.6.0.1
ibm5250 1994 kaixubuntu  mem    REG               8,10   372012  176107 /usr/lib32/libXt.so.6.0.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    96676  175893 /usr/lib32/libXmu.so.6.2.0
ibm5250 1994 kaixubuntu  mem    REG               8,10  2349356  174941 /usr/lib32/libXm.so.3.0.2
ibm5250 1994 kaixubuntu  mem    REG               8,10     9584  174877 /usr/lib32/gconv/IBM037.so
ibm5250 1994 kaixubuntu  mem    REG               8,10    17712  176095 /usr/lib32/libXfixes.so.3.1.0
ibm5250 1994 kaixubuntu  mem    REG               8,10    38520  176105 /usr/lib32/libXrender.so.1.3.0
ibm5250 1994 kaixubuntu  mem    REG               8,10   126152  139608 /lib32/ld-2.13.so
ibm5250 1994 kaixubuntu    0u   CHR              136,0      0t0       3 /dev/pts/0
ibm5250 1994 kaixubuntu    1u   CHR              136,0      0t0       3 /dev/pts/0
ibm5250 1994 kaixubuntu    2u   CHR              136,0      0t0       3 /dev/pts/0
ibm5250 1994 kaixubuntu    3u  unix 0x0000000000000000      0t0   10233 socket
ibm5250 1994 kaixubuntu    4u  unix 0x0000000000000000      0t0   10237 socket
ibm5250 1994 kaixubuntu    5u  IPv4              13351      0t0     TCP xubuntu.local:41586->192.168.1.10:telnet (ESTABLISHED)

```

---

### Post by kuzekeisai on 2013-09-12
Interesting script. Thank you n8bounds for creating it.
I already tried installing iSeries Access manually in Ubuntu 12.04, it didn't work.

About to try it in an online cloud VM Ubuntu 13.04 at [https://koding.com/?r=kuze](https://koding.com/?r=kuze)
as part of an online IBM mainframe and DEC mini computer network virtualisation project.

So, it is highly possible 
I will be back here either with a screen full of errors or a success report :)

---

### Post by princefarhaan on 2014-08-20
It appears that the old versions of libmotif and libstdc have been removed. I have updated the script to reflect the changes in the filenames and can confirm it to be working in my linux mint Qiana OS but should work for all ubuntu machines as well. Thanks is due to the originator/coder of the script. Just giving it back to our wonderful community of Linux users :-)

Just copy the below code into a file named installIBM5250.sh(you can call it whatever you want and don't forget to mark it as executable) and keep the downloaded iseries rpm in the same folder, then run "sudo ./installIBM5250.sh iSeriesAccess-7.1.0-1.0.i386.rpm"


#!/bin/bash


function usagedie {
echo '' 1>&2
echo "iSeries Client Access RPM Installer for Ubuntu" 1>&2
echo "Usage: $0 <filename.rpm>" 1>&2
echo "Example: $0 iSeriesAccess-6.1.0-1.0.i386.rpm" 1>&2
echo '' 1>&2
exit
}

function installit64 {
sudo aptitude install alien odbcinst1debian1 unixodbc libmotif3 msttcorefonts ttf-mscorefonts-installer ia32-libs -y

if [ -d /usr/lib32 ]; then
echo ''
else
sudo mkdir /usr/lib32
fi

wget [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-25ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-25ubuntu4_i386.deb)
wget [http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-4_i386.deb)

ar vx libstdc++5_3.3.6-25ubuntu4_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libstdc++.so.* /usr/lib32;
ar vx libmotif3_2.2.3-4_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libXm.so.3* /usr/lib32;

sudo alien --scripts -g $TARGETRPM
cd iSeriesAccess-*
sudo dpkg-buildpackage -b -d -ai386
sudo locale-gen en_US
cd ..
sudo dpkg -i --force-architecture iseriesaccess_*.deb
}

function installit32 {
sudo aptitude install alien odbcinst1debian1 unixodbc libmotif3 msttcorefonts ttf-mscorefonts-installer -y

wget [http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-25ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-25ubuntu4_i386.deb)
wget [http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/o/openmotif/libmotif3_2.2.3-4_i386.deb)

ar vx libstdc++5_3.3.6-25ubuntu4_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libstdc++.so.* /usr/lib;
ar vx libmotif3_2.2.3-4_i386.deb; tar xzf data.tar.gz; sudo mv usr/lib/libXm.so.3* /usr/lib;

sudo alien --scripts -g $TARGETRPM
cd iSeriesAccess-*
sudo dpkg-buildpackage -b -d -ai386
sudo locale-gen en_US
cd ..
sudo dpkg -i iseriesaccess_*.deb
}

function cleanup {
cd ..
sudo rm -rf tmpiseriesrpm
}

function goodbye {
echo ''
echo "Script complete!"
echo ''
echo "Launch the program like this:"
echo "ibm5250 192.168.156.whatever -title MyFancyTitleBar -DISPLAY_NAME \"UBUNTUA UBUNTUB UBUNTUC UBUNTUD\" -LANGID en_US"
echo ''
echo "Uninstall the program like this:"
echo "sudo dpkg --remove iseriesaccess"
echo ''
}

if [ "$1" == "" ]; then
usagedie
fi

TARGETRPM=$1

if [ -d tmpiseriesrpm ]; then
sudo rm -rf tmpiseriesrpm
else
echo ''
fi

mkdir tmpiseriesrpm
cp $TARGETRPM tmpiseriesrpm
cd tmpiseriesrpm

MYARCH=`uname -m`

if [ "$MYARCH" == "x86_64" ]; then
installit64
else
installit32
fi

cleanup
goodbye

---

