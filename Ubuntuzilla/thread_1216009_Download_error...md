---
title: "Download error.."
date: 2009-07-17
forum: Ubuntuzilla
---

### Post by pjalegria on 2009-07-17
I get that: 
> Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Failed to retrieve list of localizations. This may be due to transient network problems, so try again later. If the problem persists, please seek help on our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)


How can i fix that?

---

### Post by pjalegria on 2009-07-18
Bump...

---

### Post by omegamormegil on 2009-07-18
I get this too.  I've been trying to use this script for about 4 days, and keep getting these connection errors.
> me@mylappy:~$ ubuntuzilla.py -a install -p firefox

Welcome to the Ubuntuzilla Firefox script version 4.6.1

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.1. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/](ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Download error. Trying again, hoping for a different mirror.
Failed to retrieve list of localizations. This may be due to transient network problems, so try again later. If the problem persists, please seek help on our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by nanotube on 2009-07-21
Hi
cannot reproduce that, everything works for me here... is it possible that there were some problems on the mozilla release mirrors...?

---

### Post by omegamormegil on 2009-07-21
I still get the same errors.  Any suggestions?

---

### Post by nanotube on 2009-07-21
> **omegamormegil said:**
> I still get the same errors.  Any suggestions?

hmm, is it possible that you have a firewall blocking the default ftp port for outgoing connections?

can you manually ftp to releases.mozilla.org, say, and see if you can connect ok, and browse the directory tree, etc.?

---

### Post by omegamormegil on 2009-07-21
Well, it turns out that the Ubuntu Netbook remix doesn't install ftp (or command-not-found) by default.  I also had to manually install w3m, which wasn't installed.  Perhaps you should make these dependencies of the script.  So, if you are having this same problem, try 

> sudo aptitude install ftp w3m

So, I'm getting a lot further, but now I'm getting hung on the fact that I'm failing the 1GB free space check, which is artificially huge.  I work with give or take 200MB free space on / all the time, as I'm currently using a 4GB SSD in this netbook.  I've freed up about 400MB for this process, but I'm still getting stuck.  I'm going to have to manually disable that free space checker script to get this working.

---

### Post by omegamormegil on 2009-07-21
Success!  After neutering the free disk space check function, the script upgraded me to Firefox 3.5 like a charm.  Thanks!

---

### Post by nanotube on 2009-07-22
Hi
glad you got it working :) that said, i probably should make the error messages more useful.

all the linux installs i've ever seen have always had w3m in the default install, so i didn't even think of adding them as dependencies. 

while i am at it... should i also add tar, md5sum, gpg, and wget, in case they come out with an "ubuntu toaster remix" which has nothing but a kernel and a shell? :)

as to "neutering" the backup function - there is a commandline argument available, "--skipbackup", which would skip the backup process, and thereby also the disk space check. so for the future, you might find that helpful. :) try "ubuntuzilla.py -h" for a full list of options.

---

### Post by nanotube on 2009-07-22
Well... i added some more informative error messages, and also added dependencies for w3m, tar, and wget (for just in case).

Latest code is in git ([http://ubuntuzilla.git.sourceforge.net/git/gitweb.cgi?p=ubuntuzilla](http://ubuntuzilla.git.sourceforge.net/git/gitweb.cgi?p=ubuntuzilla)), will try to make a release in a bit.

---

### Post by omegamormegil on 2009-07-22
Don't forget the ftp dependency.

---

### Post by nanotube on 2009-07-22
> **omegamormegil said:**
> Don't forget the ftp dependency.

ubuntuzilla doesn't use ftp, we use wget. :)

---

### Post by ztmike on 2009-07-23
Getting a error trying to upgrade..not sure what to do?

> Downloading Firefox archive from the Mozilla site

--2009-07-23 00:01:22--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2)
           => `firefox-3.5.1.tar.bz2'
Resolving releases.mozilla.org... 204.152.184.196, 202.177.202.154, 129.101.198.59, ...
Connecting to releases.mozilla.org|204.152.184.196|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US ... done.
==> SIZE firefox-3.5.1.tar.bz2 ... 9876366
==> PASV ... couldn't connect to 204.152.184.196 port 52055: Connection refused
wget -c --tries=5 --read-timeout=20 --waitretry=10 [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2)
Previous command has failed to complete successfully. Exiting.
Process returned code 1
Error downloading. Trying again, hoping for a different mirror.
--2009-07-23 00:01:25--  [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2)
           => `firefox-3.5.1.tar.bz2'
Resolving mozilla.isc.org... 204.152.184.113
Connecting to mozilla.isc.org|204.152.184.113|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US ... done.
==> SIZE firefox-3.5.1.tar.bz2 ... 9876366
==> PASV ... done.    ==> RETR firefox-3.5.1.tar.bz2 ... done.
Length: 9876366 (9.4M)

100%[======================================>] 9,876,366   2.23M/s   in 5.0s    

2009-07-23 00:01:32 (1.87 MB/s) - `firefox-3.5.1.tar.bz2' saved [9876366]


Downloading Firefox signature from the Mozilla site

--2009-07-23 00:01:32--  [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2.asc](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US/firefox-3.5.1.tar.bz2.asc)
           => `firefox-3.5.1.tar.bz2.asc'
Resolving releases.mozilla.org... 128.61.111.9, 64.50.236.214, 131.188.12.212, ...
Connecting to releases.mozilla.org|128.61.111.9|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/3.5.1/linux-i686/en-US ... done.
==> SIZE firefox-3.5.1.tar.bz2.asc ... 194
==> PASV ... done.    ==> RETR firefox-3.5.1.tar.bz2.asc ... done.
Length: 194

100%[======================================>] 194         --.-K/s   in 0.01s   

2009-07-23 00:01:33 (15.1 KB/s) - `firefox-3.5.1.tar.bz2.asc' saved [194]

tru::1:1248325074:0:3:1:5
pub:-:1024:17:696E34310E3606D9:2005-09-29:::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:e:1024:17:C660CCE21AF32821:2005-09-29:2006-09-29:::::s:
sub:-:2048:16:70474DABAFE99880:2005-09-29::::::e:
tru::1:1248325074:0:3:1:5
pub:-:1024:17:74474499812347DD:2007-07-17:2011-07-20::-:Mozilla Software Releases <releases@mozilla.org>::scESC:
sub:-:1024:17:B57B548417785FE8:2007-07-17:2011-07-20:::::s:
sub:-:2048:16:CB3A74DF1B0EC2E7:2007-07-17:2011-07-20:::::e:

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Wed 15 Jul 2009 09:54:01 PM CDT using DSA key ID 17785FE8
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8D6F 1BA4 A340 4DDB 3F2F  D080 7447 4499 8123 47DD
     Subkey fingerprint: 3338 E6BA FF10 3B3D A6A9  E424 B57B 5484 1778 5FE8
sudo dpkg -L firefox |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'
Failed to determine plugin path. Exiting.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1110, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 546, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 716, in linkPlugins
    self.pluginPath = self.util.getSystemOutput(executionstring="sudo dpkg -L " + self.aptPackage + " |egrep 'firefox(-[0-9]\.[0-9]+[a-z][0-9]+)?/plugins$'", errormessage="Failed to determine plugin path. Exiting.")
  File "/usr/local/bin/ubuntuzilla.py", line 118, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
mike@Main:~$ Using 9.04 Ubuntu 64bit

---

### Post by shelfoo on 2009-07-23
Hi, I received the same error. Fix turned out to be setting "correct" ownership of your /home/<username>/.gnupg directory.

Specifically you need to make it accessible to root:
```
chown root.root /home/<username>/.gnupg -R
```

This will fix the problem for you.

In a semi related note there's a bug in the ubuntuzilla.py script that causes a crash in this particular case (on the amd64 package) - anybody know where I should send a patch?

---

### Post by nanotube on 2009-07-23
> **ztmike said:**
> Getting a error trying to upgrade..not sure what to do?

Using 9.04 Ubuntu 64bit

hi
i'm looking at your error log, you seem to be using an older version of ubuntuzilla. please get the newest version from the website and try again.

---

### Post by ztmike on 2009-07-23
> **nanotube said:**
> hi
i'm looking at your error log, you seem to be using an older version of ubuntuzilla. please get the newest version from the website and try again.

Do you have a link? n/m found it in your links under your name: [http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)

Is this new download going to overwrite the old one? I don't want the old file just sitting on my computer.

---

### Post by ztmike on 2009-07-23
Okay..ya it over written the old script.. 

It downloaded fine and updated fine..but now when I try to browse any website it won't connect to any of them and I get a "Server not found" error ? wtf is going on now? I tried rebooting my computer and even rebooting my router..which shouldn't of been the problem anyway since my other computer (this one) was/is working.

*I'm using my other computer to type this..which updated fine using your script :/

---

### Post by ztmike on 2009-07-23
I got it..thanks to a user in this forum: [http://ubuntuforums.org/showthread.php?t=1136912](http://ubuntuforums.org/showthread.php?t=1136912)

This got it working

> Try switching **network.dns.disableIPv6** option to **true** in your *about:config*. That's what solved similar problem of mine.

This forum for this script needs a FAQ or something..

---

### Post by nanotube on 2009-07-23
> **ztmike said:**
> I got it..thanks to a user in this forum: [http://ubuntuforums.org/showthread.php?t=1136912](http://ubuntuforums.org/showthread.php?t=1136912)

This got it working



This forum for this script needs a FAQ or something..

Great to hear it worked out. :)

The FAQ is an excellent idea. I'll start a FAQ page on the ubuntuzilla wiki later this evening - in the meantime, please post your ideas here as to what issues should make it to the faq. :)

---

### Post by ztmike on 2009-07-23
> **nanotube said:**
> 

The FAQ is an excellent idea. I'll start a FAQ page on the ubuntuzilla wiki later this evening - in the meantime, please post your ideas here as to what issues should make it to the faq. :)

The only things I can think of would be the 2 problems I had (that I said in this thread) 

The "Server not found" error with Firefox not being able to go to any websites seems like its a 64bit problem..being that my 32bit Ubuntu computer didn't have any problems like that...not sure what I would of done if I didn't have another computer to find out the problem. :/ 

But overall man..very nice job on the script..I'm a total Linux noob and this did wonders. All I ask is that you keep it updated. (If you even need to do that?) Should be all automatic now? I dunno..lol 

Maybe you can start a thread here and ask for input on a FAQ.

---

### Post by nanotube on 2009-07-29
Hi
just fyi - check out the new ubuntuzilla website, and the separate FAQ page, which now includes the ipv6 fix :)

thanks for the compliments - and please feel free to let me know if you run into any other issues

also, indeed, it's generic enough now that i don't really need to do anything with it from release to release. just tinkering with it for minor cosmetic fixes etc. :)

---

### Post by Samhain77 on 2009-08-12
I had the same error as the first post of this topic when the script tries to retrieve localization options...

It seems running with root permission is not showing this error... so I figured out the the problem is the output of the w3m -dump command... these are the output it gives when launching ubuntuzilla.py with -d options:

as normal users:

```
Please enter 'y' or 'n': y
['FTP Listing of /pub/mozilla.org/firefox/releases/3.5.2/linux-i686/ at\n', 'mozilla.isc.org\n', '\n', '\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\n', 'Parent Directory\n', '\n', 'Jul 31 2009 00:27    Directory af\n', 'Jul 31 2009 00:27    Directory ar\n', 'Jul 31 2009 00:27    Directory as\n', 'Jul 31 2009 00:27    Directory be\n', 'Jul 31 2009 00:27    Directory bg\n', 'Jul 31 2009 00:27    Directory bn-BD\n', 'Jul 31 2009 00:27    Directory bn-IN\n', 'Jul 31 2009 00:27    Directory ca\n', 'Jul 31 2009 00:27    Directory cs\n', 'Jul 31 2009 00:27    Directory cy\n', 'Jul 31 2009 00:27    Directory da\n', 'Jul 31 2009 00:27    Directory de\n', 'Jul 31 2009 00:27    Directory el\n', 'Jul 31 2009 00:27    Directory en-GB\n', 'Jul 31 2009 00:27    Directory en-US\n', 'Jul 31 2009 00:27    Directory eo\n', 'Jul 31 2009 00:27    Directory es-AR\n', 'Jul 31 2009 00:27    Directory es-CL\n', 'Jul 31 2009 00:27    Directory es-ES\n', 'Jul 31 2009 00:27    Directory es-MX\n', 'Jul 31 2009 00:27    Directory et\n', 'Jul 31 2009 00:27    Directory eu\n', 'Jul 31 2009 00:27    Directory fa\n', 'Jul 31 2009 00:27    Directory fi\n', 'Jul 31 2009 00:27    Directory fr\n', 'Jul 31 2009 00:27    Directory fy-NL\n', 'Jul 31 2009 00:27    Directory ga-IE\n', 'Jul 31 2009 00:27    Directory gl\n', 'Jul 31 2009 00:27    Directory gu-IN\n', 'Jul 31 2009 00:27    Directory he\n', 'Jul 31 2009 00:27    Directory hi-IN\n', 'Jul 31 2009 00:27    Directory hr\n', 'Jul 31 2009 00:27    Directory hu\n', 'Jul 31 2009 00:27    Directory id\n', 'Jul 31 2009 00:27    Directory is\n', 'Jul 31 2009 00:27    Directory it\n', 'Jul 31 2009 00:27    Directory ja\n', 'Jul 31 2009 00:27    Directory ka\n', 'Jul 31 2009 00:27    Directory kk\n', 'Jul 31 2009 00:27    Directory kn\n', 'Jul 31 2009 00:27    Directory ko\n', 'Jul 31 2009 00:27    Directory ku\n', 'Jul 31 2009 00:27    Directory lt\n', 'Jul 31 2009 00:27    Directory lv\n', 'Jul 31 2009 00:27    Directory mk\n', 'Jul 31 2009 00:27    Directory ml\n', 'Jul 31 2009 00:27    Directory mn\n', 'Jul 31 2009 00:27    Directory mr\n', 'Jul 31 2009 00:27    Directory nb-NO\n', 'Jul 31 2009 00:27    Directory nl\n', 'Jul 31 2009 00:27    Directory nn-NO\n', 'Jul 31 2009 00:27    Directory oc\n', 'Jul 31 2009 00:27    Directory or\n', 'Jul 31 2009 00:27    Directory pa-IN\n', 'Jul 31 2009 00:27    Directory pl\n', 'Jul 31 2009 00:27    Directory pt-BR\n', 'Jul 31 2009 00:27    Directory pt-PT\n', 'Jul 31 2009 00:27    Directory rm\n', 'Jul 31 2009 00:27    Directory ro\n', 'Jul 31 2009 00:27    Directory ru\n', 'Jul 31 2009 00:27    Directory si\n', 'Jul 31 2009 00:27    Directory sk\n', 'Jul 31 2009 00:27    Directory sl\n', 'Jul 31 2009 00:27    Directory sq\n', 'Jul 31 2009 00:27    Directory sr\n', 'Jul 31 2009 00:27    Directory sv-SE\n', 'Jul 31 2009 00:28    Directory ta\n', 'Jul 31 2009 00:27    Directory ta-LK\n', 'Jul 31 2009 00:28    Directory te\n', 'Jul 31 2009 00:28    Directory th\n', 'Jul 31 2009 00:28    Directory tr\n', 'Jul 31 2009 00:28    Directory uk\n', 'Jul 31 2009 00:28    Directory vi\n', 'Jul 30 2009 09:29    Directory xpi\n', 'Jul 31 2009 00:28    Directory zh-CN\n', 'Jul 31 2009 00:28    Directory zh-TW\n', '\n', '\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\xe2\x94\x81\n']
Retrieving list of available localizations for Firefox ...
w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
[]
Download error. Trying again, hoping for a different mirror.

```

as root:
```
['Index of ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.2/\n', 'linux-i686/\n', '\n', '[Upper Directory]\n', 'af/. . . . . . . . . Jul 31 00:27\n', 'ar/. . . . . . . . . Jul 31 00:27\n', 'as/. . . . . . . . . Jul 31 00:27\n', 'be/. . . . . . . . . Jul 31 00:27\n', 'bg/. . . . . . . . . Jul 31 00:27\n', 'bn-BD/ . . . . . . . Jul 31 00:27\n', 'bn-IN/ . . . . . . . Jul 31 00:27\n', 'ca/. . . . . . . . . Jul 31 00:27\n', 'cs/. . . . . . . . . Jul 31 00:27\n', 'cy/. . . . . . . . . Jul 31 00:27\n', 'da/. . . . . . . . . Jul 31 00:27\n', 'de/. . . . . . . . . Jul 31 00:27\n', 'el/. . . . . . . . . Jul 31 00:27\n', 'en-GB/ . . . . . . . Jul 31 00:27\n', 'en-US/ . . . . . . . Jul 31 00:27\n', 'eo/. . . . . . . . . Jul 31 00:27\n', 'es-AR/ . . . . . . . Jul 31 00:27\n', 'es-CL/ . . . . . . . Jul 31 00:27\n', 'es-ES/ . . . . . . . Jul 31 00:27\n', 'es-MX/ . . . . . . . Jul 31 00:27\n', 'et/. . . . . . . . . Jul 31 00:27\n', 'eu/. . . . . . . . . Jul 31 00:27\n', 'fa/. . . . . . . . . Jul 31 00:27\n', 'fi/. . . . . . . . . Jul 31 00:27\n', 'fr/. . . . . . . . . Jul 31 00:27\n', 'fy-NL/ . . . . . . . Jul 31 00:27\n', 'ga-IE/ . . . . . . . Jul 31 00:27\n', 'gl/. . . . . . . . . Jul 31 00:27\n', 'gu-IN/ . . . . . . . Jul 31 00:27\n', 'he/. . . . . . . . . Jul 31 00:27\n', 'hi-IN/ . . . . . . . Jul 31 00:27\n', 'hr/. . . . . . . . . Jul 31 00:27\n', 'hu/. . . . . . . . . Jul 31 00:27\n', 'id/. . . . . . . . . Jul 31 00:27\n', 'is/. . . . . . . . . Jul 31 00:27\n', 'it/. . . . . . . . . Jul 31 00:27\n', 'ja/. . . . . . . . . Jul 31 00:27\n', 'ka/. . . . . . . . . Jul 31 00:27\n', 'kk/. . . . . . . . . Jul 31 00:27\n', 'kn/. . . . . . . . . Jul 31 00:27\n', 'ko/. . . . . . . . . Jul 31 00:27\n', 'ku/. . . . . . . . . Jul 31 00:27\n', 'lt/. . . . . . . . . Jul 31 00:27\n', 'lv/. . . . . . . . . Jul 31 00:27\n', 'mk/. . . . . . . . . Jul 31 00:27\n', 'ml/. . . . . . . . . Jul 31 00:27\n', 'mn/. . . . . . . . . Jul 31 00:27\n', 'mr/. . . . . . . . . Jul 31 00:27\n', 'nb-NO/ . . . . . . . Jul 31 00:27\n', 'nl/. . . . . . . . . Jul 31 00:27\n', 'nn-NO/ . . . . . . . Jul 31 00:27\n', 'oc/. . . . . . . . . Jul 31 00:27\n', 'or/. . . . . . . . . Jul 31 00:27\n', 'pa-IN/ . . . . . . . Jul 31 00:27\n', 'pl/. . . . . . . . . Jul 31 00:27\n', 'pt-BR/ . . . . . . . Jul 31 00:27\n', 'pt-PT/ . . . . . . . Jul 31 00:27\n', 'rm/. . . . . . . . . Jul 31 00:27\n', 'ro/. . . . . . . . . Jul 31 00:27\n', 'ru/. . . . . . . . . Jul 31 00:27\n', 'si/. . . . . . . . . Jul 31 00:27\n', 'sk/. . . . . . . . . Jul 31 00:27\n', 'sl/. . . . . . . . . Jul 31 00:27\n', 'sq/. . . . . . . . . Jul 31 00:27\n', 'sr/. . . . . . . . . Jul 31 00:27\n', 'sv-SE/ . . . . . . . Jul 31 00:27\n', 'ta-LK/ . . . . . . . Jul 31 00:27\n', 'ta/. . . . . . . . . Jul 31 00:28\n', 'te/. . . . . . . . . Jul 31 00:28\n', 'th/. . . . . . . . . Jul 31 00:28\n', 'tr/. . . . . . . . . Jul 31 00:28\n', 'uk/. . . . . . . . . Jul 31 00:28\n', 'vi/. . . . . . . . . Jul 31 00:28\n', 'xpi/ . . . . . . . . Jul 30 09:29\n', 'zh-CN/ . . . . . . . Jul 31 00:28\n', 'zh-TW/ . . . . . . . Jul 31 00:28\n', '\n']
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at http://ubuntuzilla.sourceforge.net/ for steps you can take to resolve this problem.]
  0. af         Afrikaans [Afrikaans]         
  1. ar         Arabic [&#1593;&#1585;&#1576;&#1610;]             
  2. as         Assamese [&#2437;&#2488;&#2478;&#2496;&#2479;&#2492;&#2494;]
  3. be         Belarusian [&#1041;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103;]
  4. bg         Bulgarian [&#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1089;&#1082;&#1080;]
  5. bn-BD      Bengali (Bangladesh) [&#2476;&#2494;&#2434;&#2482;&#2494; (&#2476;&#2494;&#2434;&#2482;&#2494;&#2470;&#2503;&#2486;)]
  6. bn-IN      Bengali (India) [&#2476;&#2494;&#2434;&#2482;&#2494; (&#2477;&#2494;&#2480;&#2468;)]
  7. ca         Catalan [català]             
  8. cs         Czech [&#268;e&#353;tina]             
  9. cy                                       
 10. da         Danish [Dansk]                
 11. de         German [Deutsch]              
 12. el         Greek [&#917;&#955;&#955;&#951;&#957;&#953;&#954;&#940;]      
 13. en-GB      English (British) [English (British)]
 14. en-US      English (US) [English (US)]   
 15. eo         Esperanto [Esperanto]         
 16. es-AR      Spanish (Argentina) [Español (de Argentina)]
 17. es-CL      Spanish (Chile) [Español (de Chile)]
 18. es-ES      Spanish (Spain) [Español (de España)]
 19. es-MX      Spanish (Mexico) [Español (de México)]
 20. et         Estonian [Eesti keel]         
 21. eu         Basque [Euskara]              
 22. fa         Persian [&#1601;&#1575;&#1585;&#1587;&#1740;]          
 23. fi         Finnish [suomi]               
 24. fr         French [Français]            
 25. fy-NL      Frisian [Frysk]               
 26. ga-IE      Irish [Gaeilge]               
 27. gl         Galician [Galego]             
 28. gu-IN      Gujarati [&#2711;&#2753;&#2716;&#2736;&#2750;&#2724;&#2752;]
 29. he         Hebrew [&#1506;&#1489;&#1512;&#1497;&#1514;]           
 30. hi-IN      Hindi (India) [&#2361;&#2367;&#2344;&#2381;&#2342;&#2368; (&#2349;&#2366;&#2352;&#2340;)]
 31. hr         Croatian [Hrvatski]           
 32. hu         Hungarian [Magyar]            
 33. id         Indonesian [Bahasa Indonesia] 
 34. is         Icelandic [íslenska]         
 35. it         Italian [Italiano]            
 36. ja         Japanese [&#26085;&#26412;&#35486;]          
 37. ka         Georgian [&#4325;&#4304;&#4320;&#4311;&#4323;&#4314;&#4312;]
 38. kk         Kazakh [&#1178;&#1072;&#1079;&#1072;&#1179;]           
 39. kn         Kannada [&#3221;&#3240;&#3277;&#3240;&#3233;]     
 40. ko         Korean [&#54620;&#44397;&#50612;]            
 41. ku         Kurdish [Kurdî]              
 42. lt         Lithuanian [lietuvi&#371; kalba]  
 43. lv         Latvian [Latvie&#353;u]           
 44. mk         Macedonian [&#1052;&#1072;&#1082;&#1077;&#1076;&#1086;&#1085;&#1089;&#1082;&#1080;]
 45. ml         Malayalam [&#3374;&#3378;&#3375;&#3390;&#3379;&#3330;]
 46. mn         Mongolian [&#1052;&#1086;&#1085;&#1075;&#1086;&#1083;]      
 47. mr         Marathi [&#2350;&#2352;&#2366;&#2336;&#2368;]     
 48. nb-NO      Norwegian (Bokmål) [Norsk bokmål]
 49. nl         Dutch [Nederlands]            
 50. nn-NO      Norwegian (Nynorsk) [Norsk nynorsk]
 51. oc         Occitan (Lengadocian) [occitan (lengadocian)]
 52. or         Oriya [&#2835;&#2849;&#2876;&#2879;&#2822;]       
 53. pa-IN      Punjabi [&#2602;&#2672;&#2588;&#2622;&#2604;&#2624;]  
 54. pl         Polish [Polski]               
 55. pt-BR      Portuguese (Brazilian) [Português (do Brasil)]
 56. pt-PT      Portuguese (Portugal) [Português (Europeu)]
 57. rm         Romansh [rumantsch]           
 58. ro         Romanian [român&#259;]           
 59. ru         Russian [&#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;]      
 60. si         Sinhala [&#3523;&#3538;&#3458;&#3524;&#3517;]     
 61. sk         Slovak [sloven&#269;ina]          
 62. sl         Slovenian [slovensko]         
 63. sq         Albanian [Shqip]              
 64. sr         Serbian [&#1089;&#1088;&#1087;&#1089;&#1082;&#1080;]        
 65. sv-SE      Swedish [Svenska]             
 66. ta-LK      Tamil (Sri Lanka) [&#2980;&#2990;&#3007;&#2996;&#3021; (&#2951;&#2994;&#2969;&#3021;&#2965;&#3016;)]
 67. ta         Tamil [&#2980;&#2990;&#3007;&#2996;&#3021;]       
 68. te         Telugu [&#3108;&#3142;&#3122;&#3137;&#3095;&#3137;]   
 69. th         Thai [&#3652;&#3607;&#3618;]              
 70. tr         Turkish [Türkçe]            
 71. uk         Ukrainian [&#1059;&#1082;&#1088;&#1072;&#1111;&#1085;&#1089;&#1100;&#1082;&#1072;]
 72. vi         Vietnamese [Ti&#7871;ng Vi&#7879;t]   
 73. zh-CN      Chinese (Simplified) [&#20013;&#25991; (&#31616;&#20307;)]
 74. zh-TW      Chinese (Traditional) [&#27491;&#39636;&#20013;&#25991; (&#32321;&#39636;)]

Enter your choice of localization (integer, from 0 to 74): 

```

It seems w3m output is different from normal to root user... and the script doesn't recognize the normal user's one.

Thanks a lot for your support....

I'm on Ubuntu 9.04 64 bit....

---

### Post by nanotube on 2009-08-12
interesting, i've never seen that behavior. maybe you have something weird in your user's w3m config? do you have anything in ~/.w3m ?

what is output if you run w3m directly, as a regular user?

```
w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.2/linux-i686/
```

and does it look any different than if you do that with sudo?

---

### Post by Samhain77 on 2009-08-13
~/.w3m folder is empty now... I've just had a look to that folder as I thought it was a w3m config problem and deleted some config files... but result still the same.

these are the results of w3m command you wrote:


as normal user:
```
FTP Listing of /pub/mozilla.org/firefox/releases/3.5.2/linux-i686/ at
mozilla.isc.org

&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;
Parent Directory

Jul 31 2009 00:27    Directory af
Jul 31 2009 00:27    Directory ar
Jul 31 2009 00:27    Directory as
Jul 31 2009 00:27    Directory be
Jul 31 2009 00:27    Directory bg
Jul 31 2009 00:27    Directory bn-BD
Jul 31 2009 00:27    Directory bn-IN
Jul 31 2009 00:27    Directory ca
Jul 31 2009 00:27    Directory cs
Jul 31 2009 00:27    Directory cy
Jul 31 2009 00:27    Directory da
Jul 31 2009 00:27    Directory de
Jul 31 2009 00:27    Directory el
Jul 31 2009 00:27    Directory en-GB
Jul 31 2009 00:27    Directory en-US
Jul 31 2009 00:27    Directory eo
Jul 31 2009 00:27    Directory es-AR
Jul 31 2009 00:27    Directory es-CL
Jul 31 2009 00:27    Directory es-ES
Jul 31 2009 00:27    Directory es-MX
Jul 31 2009 00:27    Directory et
Jul 31 2009 00:27    Directory eu
Jul 31 2009 00:27    Directory fa
Jul 31 2009 00:27    Directory fi
Jul 31 2009 00:27    Directory fr
Jul 31 2009 00:27    Directory fy-NL
Jul 31 2009 00:27    Directory ga-IE
Jul 31 2009 00:27    Directory gl
Jul 31 2009 00:27    Directory gu-IN
Jul 31 2009 00:27    Directory he
Jul 31 2009 00:27    Directory hi-IN
Jul 31 2009 00:27    Directory hr
Jul 31 2009 00:27    Directory hu
Jul 31 2009 00:27    Directory id
Jul 31 2009 00:27    Directory is
Jul 31 2009 00:27    Directory it
Jul 31 2009 00:27    Directory ja
Jul 31 2009 00:27    Directory ka
Jul 31 2009 00:27    Directory kk
Jul 31 2009 00:27    Directory kn
Jul 31 2009 00:27    Directory ko
Jul 31 2009 00:27    Directory ku
Jul 31 2009 00:27    Directory lt
Jul 31 2009 00:27    Directory lv
Jul 31 2009 00:27    Directory mk
Jul 31 2009 00:27    Directory ml
Jul 31 2009 00:27    Directory mn
Jul 31 2009 00:27    Directory mr
Jul 31 2009 00:27    Directory nb-NO
Jul 31 2009 00:27    Directory nl
Jul 31 2009 00:27    Directory nn-NO
Jul 31 2009 00:27    Directory oc
Jul 31 2009 00:27    Directory or
Jul 31 2009 00:27    Directory pa-IN
Jul 31 2009 00:27    Directory pl
Jul 31 2009 00:27    Directory pt-BR
Jul 31 2009 00:27    Directory pt-PT
Jul 31 2009 00:27    Directory rm
Jul 31 2009 00:27    Directory ro
Jul 31 2009 00:27    Directory ru
Jul 31 2009 00:27    Directory si
Jul 31 2009 00:27    Directory sk
Jul 31 2009 00:27    Directory sl
Jul 31 2009 00:27    Directory sq
Jul 31 2009 00:27    Directory sr
Jul 31 2009 00:27    Directory sv-SE
Jul 31 2009 00:28    Directory ta
Jul 31 2009 00:27    Directory ta-LK
Jul 31 2009 00:28    Directory te
Jul 31 2009 00:28    Directory th
Jul 31 2009 00:28    Directory tr
Jul 31 2009 00:28    Directory uk
Jul 31 2009 00:28    Directory vi
Jul 30 2009 09:29    Directory xpi
Jul 31 2009 00:28    Directory zh-CN
Jul 31 2009 00:28    Directory zh-TW

&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;

```

as root:
```
Index of ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.2/
linux-i686/

[Upper Directory]
af/. . . . . . . . . Jul 31 00:27
ar/. . . . . . . . . Jul 31 00:27
as/. . . . . . . . . Jul 31 00:27
be/. . . . . . . . . Jul 31 00:27
bg/. . . . . . . . . Jul 31 00:27
bn-BD/ . . . . . . . Jul 31 00:27
bn-IN/ . . . . . . . Jul 31 00:27
ca/. . . . . . . . . Jul 31 00:27
cs/. . . . . . . . . Jul 31 00:27
cy/. . . . . . . . . Jul 31 00:27
da/. . . . . . . . . Jul 31 00:27
de/. . . . . . . . . Jul 31 00:27
el/. . . . . . . . . Jul 31 00:27
en-GB/ . . . . . . . Jul 31 00:27
en-US/ . . . . . . . Jul 31 00:27
eo/. . . . . . . . . Jul 31 00:27
es-AR/ . . . . . . . Jul 31 00:27
es-CL/ . . . . . . . Jul 31 00:27
es-ES/ . . . . . . . Jul 31 00:27
es-MX/ . . . . . . . Jul 31 00:27
et/. . . . . . . . . Jul 31 00:27
eu/. . . . . . . . . Jul 31 00:27
fa/. . . . . . . . . Jul 31 00:27
fi/. . . . . . . . . Jul 31 00:27
fr/. . . . . . . . . Jul 31 00:27
fy-NL/ . . . . . . . Jul 31 00:27
ga-IE/ . . . . . . . Jul 31 00:27
gl/. . . . . . . . . Jul 31 00:27
gu-IN/ . . . . . . . Jul 31 00:27
he/. . . . . . . . . Jul 31 00:27
hi-IN/ . . . . . . . Jul 31 00:27
hr/. . . . . . . . . Jul 31 00:27
hu/. . . . . . . . . Jul 31 00:27
id/. . . . . . . . . Jul 31 00:27
is/. . . . . . . . . Jul 31 00:27
it/. . . . . . . . . Jul 31 00:27
ja/. . . . . . . . . Jul 31 00:27
ka/. . . . . . . . . Jul 31 00:27
kk/. . . . . . . . . Jul 31 00:27
kn/. . . . . . . . . Jul 31 00:27
ko/. . . . . . . . . Jul 31 00:27
ku/. . . . . . . . . Jul 31 00:27
lt/. . . . . . . . . Jul 31 00:27
lv/. . . . . . . . . Jul 31 00:27
mk/. . . . . . . . . Jul 31 00:27
ml/. . . . . . . . . Jul 31 00:27
mn/. . . . . . . . . Jul 31 00:27
mr/. . . . . . . . . Jul 31 00:27
nb-NO/ . . . . . . . Jul 31 00:27
nl/. . . . . . . . . Jul 31 00:27
nn-NO/ . . . . . . . Jul 31 00:27
oc/. . . . . . . . . Jul 31 00:27
or/. . . . . . . . . Jul 31 00:27
pa-IN/ . . . . . . . Jul 31 00:27
pl/. . . . . . . . . Jul 31 00:27
pt-BR/ . . . . . . . Jul 31 00:27
pt-PT/ . . . . . . . Jul 31 00:27
rm/. . . . . . . . . Jul 31 00:27
ro/. . . . . . . . . Jul 31 00:27
ru/. . . . . . . . . Jul 31 00:27
si/. . . . . . . . . Jul 31 00:27
sk/. . . . . . . . . Jul 31 00:27
sl/. . . . . . . . . Jul 31 00:27
sq/. . . . . . . . . Jul 31 00:27
sr/. . . . . . . . . Jul 31 00:27
sv-SE/ . . . . . . . Jul 31 00:27
ta-LK/ . . . . . . . Jul 31 00:27
ta/. . . . . . . . . Jul 31 00:28
te/. . . . . . . . . Jul 31 00:28
th/. . . . . . . . . Jul 31 00:28
tr/. . . . . . . . . Jul 31 00:28
uk/. . . . . . . . . Jul 31 00:28
vi/. . . . . . . . . Jul 31 00:28
xpi/ . . . . . . . . Jul 30 09:29
zh-CN/ . . . . . . . Jul 31 00:28
zh-TW/ . . . . . . . Jul 31 00:28

```

it seems something related to locale/regional settings or codepage... I can't understand it...

Thanks for your interest

---

### Post by Samhain77 on 2009-08-13
I've just created a test account with normal user rights and I found that the problem is the same....
I've used w3m to make dump of something like [http://www.google.com](http://www.google.com) and it produces the same result either with normal user or root...

It's all very strange....

---

### Post by Samhain77 on 2009-08-13
#-o unbelievable..... it was a proxy issue..... running w3m trough proxy server give the erroneous result... without proxy it worked.

w3m seems to use the FTP_PROXY and http_proxy environment variables... I had to set the http one and unset the FTP.

Now I'm on FF 3.5.2!!!! :popcorn:

Thanks a lot nanotube for helping me on investigate the problem

---

### Post by nanotube on 2009-08-13
good work! :)

---

### Post by fencer on 2009-11-14
I downloaded the latest seamonkey release, placed it in /tmp, but ubuntuzilla still doesn't recognizes it, I just dont know whats wrong with it...
```
david@orozco-rojas:~$ ubuntuzilla.py -a install -p seamonkey

Welcome to the Ubuntuzilla Seamonkey script version 4.7.8

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Seamonkey on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/ 

Retrieving the version of the latest release of Seamonkey from the Mozilla website...
The most recent release of Seamonkey is detected to be 2.0.

Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Seamonkey ...
w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
[]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
[]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://ftp.osuosl.org/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
[]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://mozilla.cs.utah.edu/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
[]
Download error. Trying again, hoping for a different mirror.
w3m -dump ftp://mozilla.mirrors.tds.net/pub/mozilla.org/seamonkey/releases/2.0/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
[]
Download error. Trying again, hoping for a different mirror.
```

---

### Post by nanotube on 2009-11-15
> **fencer said:**
> I downloaded the latest seamonkey release, placed it in /tmp, but ubuntuzilla still doesn't recognizes it, I just dont know whats wrong with it...


it still needs to connect to the ftp server to compare the file you have with the one available. if you can't connect to ftp, then try the slightly more manual method described here:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

