---
title: "Installing Bitdefender Antivirus gui dpgk problems"
date: 2010-04-06
forum: Security
---

### Post by mchain on 2010-04-06
I got the *.deb.ru*n package from bitdefender.com and downloaded both the .pdf file for installation instructions, and the BitDefender Data Sheet for Unices pdf.  I am not able to install this program using dpgk -i as instructed in the first pdf file.  Running the dpgk command always results in 'file or archive not found' error.  

Double clicking the file will result in terminal opening, verifying file as 'good', a EULA follows, but as the terminal is not run under 'superuser', installation will stop. 

Opening terminal as superuser and entering the commands as shown always results in 'file or archive not found' error, as specified in the first paragraph and with the commands entered as specified in the first pdf file mentioned.  I have tried many variations on these instructions provided in the installation pdf, such as "# dpgk -i Bitdefender-Anitvirus-Scanner-Gui_7.6-4.linux-gcc4x.i586,deb.run", but nothing allows dpgk to find this file under superuser priveleges.  This file is on my desktop.  For example, cd command does not do anything, as in "# cd desktop".  Bash just reports "file or command not found".  I want to install this file with the gui option as this will make it simpler for me to run this application.

I already have a free license procured for this product.  It is not going to be used for anything else other than personal use. 

My reason for doing this is because Avast for Linux simply will not update virus definitions anymore.  This has been going on since December 2009, and I tried to update the definitions one more time to no avail.  Last time the definitions updated was on March 22, 2010.  I believe the root problem is with the browser used by this program, Firefox 3.0.18, as attempting to get the vsupd4.exe file from the Avast.com site does not work 95 to 98% of the time.  I know the .exe file does not apply to Ubuntu, but this is an example, and in any case, downloading this file should not be a problem.  Avast does not supply an alternative browser to use, and will not until they provide an upgraded version of their antivirus program for linux.

Obviously, I have been in touch with avast technical support, and this is what they told me.  Support for Google Chrome is coming.

When I use Google Chrome, for example, this test download of vsupd4.exe will occur at least half the time.  

I did have a corruption issue with Firefox a while back around September of last year where I lost the both the menu bar and the title bar (I mean the File, Edit, View and Icon bar, respectively) and I figured out a workaround to get them back.  This corruption was caused by an addon update from FoxyThemes which did not complete properly.  Needless to say, I do not have this addon installed in Firefox anymore. 

How to I get dpgk to find this file?  It is on my desktop.

Thanks.  BTW the bitdefender file downloaded in firefox with no problem whatsoever.  It seems the only time I have a problem downloading is when I try to either access the avast website or, if I get in, the download page itself.  I do not have any particular problems accessing other sites on the internet.

---

### Post by FuturePilot on 2010-04-06
Please read this as anti-virus is not really needed on Ubuntu. 
[http://ubuntuforums.org/forumdisplay.php?f=338]("http://ubuntuforums.org/forumdisplay.php?f=338")

But if you decide to use anti-virus anyway try
```
chmod +x Desktop/Bitdefender-Anitvirus-Scanner-Gui_7.6-4.linux-gcc4x.i586.deb.run
sudo Desktop/Bitdefender-Anitvirus-Scanner-Gui_7.6-4.linux-gcc4x.i586.deb.run
```

Keep in mind Linux is case sensitive so "desktop" is not the same as "Desktop" is not the same as "DeSkToP".

---

### Post by BigCityCat on 2010-04-06
This is the easiest way to install it, and by the way I use it to scan my windows drive if I have a problem. 

[http://download.bitdefender.com/repos/](http://download.bitdefender.com/repos/)

---

### Post by mchain on 2010-04-19
Thank you both for getting back so soon.  

I tried using terminal copy and paste the exact commands.  Result: "No such file or directory found."

Did not work.

I would try the repository command but the link provided just gives me the repository location, not a way to install via Synaptic Package Manager, which I would prefer.

I have been busy, so I got back as soon as I could.

---

### Post by cariboo on 2010-04-19
It may be easier to run the chmod command in the directory the package is in.

```
chmod +x ./*run
```

Then:

```
./*run
```

then right click the package and use open with Gdebi package installer, after the .run file has been unpacked.

---

### Post by lisati on 2010-04-19
Just a thought, are you doing **cd desktop** or **cd Desktop**?

---

### Post by cariboo on 2010-04-19
That assumes that file is on the desktop, since Karmic at least, all downloads go to ~/Downloads, unless you specifically tell Firefox/Chrome, whatever browser you are using, to save the file elsewhere.

---

