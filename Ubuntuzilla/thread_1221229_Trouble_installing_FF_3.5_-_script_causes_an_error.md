---
title: "Trouble installing FF 3.5 - script causes an error"
date: 2009-07-23
forum: Ubuntuzilla
---

### Post by ThAixStYLe on 2009-07-23
here's my output for the area in question:
[INDENT]
Resolving releases.mozilla.org... 155.98.64.83, 204.246.0.136, 64.50.236.52, ...
Connecting to releases.mozilla.org|155.98.64.83|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US ... 
No such directory `pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US'.

wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1151, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 211, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 238, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 604, in install
    self.downloadPackage()
  File "/usr/local/bin/ubuntuzilla.py", line 773, in downloadPackage
    self.util.robustDownload(argsdict={'executionstring':"wget -c --tries=5 --read-timeout=20 --waitretry=10 ftp://" + "%mirror%" + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/"+ self.locList[self.locChoice] + "/" + self.packageFilename, 'includewithtest':True})
  File "/usr/local/bin/ubuntuzilla.py", line 155, in robustDownload
    self.execSystemCommand(**argsdict)
  File "/usr/local/bin/ubuntuzilla.py", line 141, in execSystemCommand
    print >>sys.stderr, result
NameError: global name 'result' is not defined[/INDENT]

Any ideas?

---

### Post by nanotube on 2009-07-23
Hi

thanks for reporting this!

yes, ideas - made a stupid mistake in my last revision :|

here, grab this latest version from this bug tracker thread:
[https://sourceforge.net/tracker/?func=detail&aid=2825626&group_id=202789&atid=982990](https://sourceforge.net/tracker/?func=detail&aid=2825626&group_id=202789&atid=982990)

(.deb listed under file attachments)

it fixes this bug, as well as a couple of others.

---

### Post by Taladel on 2009-07-24
I was unable to open the new .deb file. "ubuntuzilla-4.6.2-0ubuntu1-i386.deb" still works just fine, but 4.6.3 gave me an error in gdebi. Archive Manager handled it fine though.

---

### Post by Elinor on 2009-07-24
I get the same problem with Gdebi installer, but I haven't managed to work around it using archive manager, can anyone suggest how to get it to install with GDebi? I have changed the permissions on the file but no luck.

I get the following notice...

"The package may be corrupted or you are not allowed to open the file. Check the permissions of the file"

Thanks

---

### Post by nanotube on 2009-07-24
hmm, maybe the bug tracker has corrupted the file on upload...
you could grab the latest source snapshot from the git repository, unzip it, and from within that directory run "python build-distribution.py", which will build a .deb for you from the sources. 

not at my comp right now, but will try to do the same in a bit and attach the .deb here.

---

### Post by nanotube on 2009-07-24
Ok, it does look like the packages attached to that bug tracker are corrupted.

Here are some fresh-built uncorrupted packages, attached, along with their md5sums.

---

### Post by figdrewton on 2009-07-24
Thanks, I was having the same issue but this update worked perfectly. I'm posting this using FF 3.5.1 now!

---

### Post by Yakuza on 2009-07-24
Thanks, i had the same problem and 4.6.3 worked great :)

---

### Post by Taladel on 2009-07-25
Worked perfectly, thanks very much!

---

### Post by Elinor on 2009-07-25
Worked perfectly for me too, many thanks.

I still have Shiretoko but I can cope with that for a few months until the next Ubuntu comes out.

:D

---

### Post by hebert88 on 2009-07-25
Yesss!! Perfect!
I am Brazilian and I do not speak almost no English .. and I am translating this text with the help of google .. lol
I did download ubuntuzilla 4.6.2 and could not upgrade Firefox, but with 4.6.3 everything was right.
Thanks!

---

### Post by zeddock on 2009-07-26
Error here.  Used 64bit version but cannot get past this.

zeddock


gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.

---

### Post by nanotube on 2009-07-26
> **zeddock said:**
> Error here.  Used 64bit version but cannot get past this.

zeddock


gpg --keyserver keymaster.veridis.com --recv 0E3606D9 812347DD
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Unable to retrieve Mozilla Software Releases Public key from keymaster.veridis.com . Trying again...
Failed to retrieve Mozilla Software Releases Public key from any of the listed keyservers. Please check your network connection, and try again later.

could be due to firewall blocking gpg server port.

as a quick workaround, run with "-g" option to bypass gpg signature checking.

---

### Post by nanotube on 2009-07-26
just a notice that i have made the 4.6.3 release, so, there's no longer a need to get your debs from here - get them straight from the source. :)

---

