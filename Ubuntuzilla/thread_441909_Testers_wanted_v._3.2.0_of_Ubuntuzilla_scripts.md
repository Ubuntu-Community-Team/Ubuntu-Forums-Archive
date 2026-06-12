---
title: "Testers wanted: v. 3.2.0 of Ubuntuzilla scripts"
date: 2007-05-13
forum: Ubuntuzilla
---

### Post by nanotube on 2007-05-13
using the update idea from user *sumashod*, and some code refactoring, i have made the next version of all 3 scripts. 

new features include:
* the '-update' action, which checks if a version newer than the one installed exists, and if so, offers to update (for ff and tb, simply encourages the user to use built in updater)
* the '-t' option, which makes the script do a 'dry run' where nothing actually gets done. i used it to test the script framework, but without messing with my system. it's very nice for testing, but not really a useful feature from a user's standpoint. :)
* buglet fix in seamonkey: the message pointing out the installable language packs was accidentally included after removal, not after installation.

please test the new scripts, everyone, and report anything that doesn't work as expected.

to run with with testing option, you can use,
```
bash /path/to/script -install -t
bash /path/to/script -remove -t
bash /path/to/script -update -t

```

but i have already done that... now, i'd like to have some light 'live' testing to make sure everything works. :) to run the script so that it actually does something, use
```
bash /path/to/script -install
bash /path/to/script -remove
bash /path/to/script -update

```

---

### Post by nanbudh on 2007-05-14
ok i did what u said. i downloaded installnewfirefox.sh and ran it in the terminal. it started its work and finished with after giving a message that latest firefox was installed. but when i run thwe firefox and check its About tab it still shows me the old version ie. 1.5.0.9. i even restarted the computer but still the it shows the older version. :( Could this be because i was running an instance of firefox when the script was downloading new version? what went wrong?

---

### Post by nanotube on 2007-05-14
> **nanbudh said:**
> ok i did what u said. i downloaded installnewfirefox.sh and ran it in the terminal. it started its work and finished with after giving a message that latest firefox was installed. but when i run thwe firefox and check its About tab it still shows me the old version ie. 1.5.0.9. i even restarted the computer but still the it shows the older version. :( Could this be because i was running an instance of firefox when the script was downloading new version? what went wrong?

hmmm... strange. could you please post the output of the following command:
```
ls -al /usr/bin/firefox
```

---

### Post by nanotube on 2007-05-14
> **nanbudh said:**
> ok i did what u said. i downloaded installnewfirefox.sh and ran it in the terminal. it started its work and finished with after giving a message that latest firefox was installed. but when i run thwe firefox and check its About tab it still shows me the old version ie. 1.5.0.9. i even restarted the computer but still the it shows the older version. :( Could this be because i was running an instance of firefox when the script was downloading new version? what went wrong?
oh, and did you by any chance run it with the '-t' option, maybe?

---

### Post by nanbudh on 2007-05-14
here is the output from the command 'ls -al /usr/bin/firefox:
 lrwxrwxrwx 1 root root 22 2007-01-30 17:23 /usr/bin/firefox -> ../lib/firefox/firefox
And yes i did run it with t option! was that the reason? what does the t option do?

---

### Post by nanotube on 2007-05-14
> **nanbudh said:**
> here is the output from the command 'ls -al /usr/bin/firefox:
 lrwxrwxrwx 1 root root 22 2007-01-30 17:23 /usr/bin/firefox -> ../lib/firefox/firefox
And yes i did run it with t option! was that the reason? what does the t option do?

hehe well that explains it. please re-read the first post in this thread carefully! the -t option is "testing" which basically means the script does a dry run, without actually installing firefox!
so just run it again without '-t' option in order to actually install. :)

---

### Post by coolcar on 2007-05-15
Hi Nanbudh,

I ran the script and got the message "new Firefox version 2.0.0.3 has been installed successfully. Thank you for using Ubuntuzilla scripts."

However I noticed that the first time I came out of browser and reloaded it I think :confused: it was still on the older version.  But the next time it was good news :) - I opened it up it came with a message that "Firefox is not your default browser. Do you want to set it .."

ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2007-05-15 20:29 /usr/bin/firefox -> /opt/firefox/firefox

By the way - If we download the script on the FAQ community site then the file downloaded has got version number in front of it and if users will cut an paste the command then they will get the "file not found" error. However no such issue here as the filenameA is stored without the version suffix.

Now I will try to run the Thunderbird script.

Thanks. You are a :KS

---

### Post by nanbudh on 2007-05-15
I re ran the script without the t option and after the step where  it asked for localisation this is was the console output:
***************
Updating repositories list

Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Ign [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Release.gpg
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:9 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release

Hit [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:10 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release [745B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Ign [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Ign [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages [177kB]
99% [Waiting for headers] [Waiting for headers] [Connecting to wxpython.wxcommunity.com (209.216.209.163)]
gzip: stdin: not in gzip format
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
  Sub-process gzip returned an error code (1)
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Packages
Hit [http://wxpython.wxcommunity.com](http://wxpython.wxcommunity.com)  Sources
Fetched 945B in 4s (203B/s)
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
************************************************
So then  i ran apt-get update and it gave same output. whats happening?
Earlier when i had run the script with t option it had given a final message that latest firefox was installed. what happened now? Is this a problem with some packages not being found? I dont get it. Please help.

---

### Post by nanotube on 2007-05-15
> **coolcar said:**
> Hi Nanbudh,

I ran the script and got the message "new Firefox version 2.0.0.3 has been installed successfully. Thank you for using Ubuntuzilla scripts."

However I noticed that the first time I came out of browser and reloaded it I think :confused: it was still on the older version.  But the next time it was good news :) - I opened it up it came with a message that "Firefox is not your default browser. Do you want to set it .."

ls -al /usr/bin/firefox
lrwxrwxrwx 1 root root 20 2007-05-15 20:29 /usr/bin/firefox -> /opt/firefox/firefox

By the way - If we download the script on the FAQ community site then the file downloaded has got version number in front of it and if users will cut an paste the command then they will get the "file not found" error. However no such issue here as the filenameA is stored without the version suffix.

Now I will try to run the Thunderbird script.

Thanks. You are a :KS

glad it worked out for you. ;) the reason there's a version number appended to the filename on the main site is that the sourceforge fileservers require unique filenames for releases, so i have to add a v.number. that's why the instructions on the homepage say "save the file as installnewfirefox.sh" and such. :)

please report your results from the thunderbird script - let me know if it worked as expected, or not.

---

### Post by nanotube on 2007-05-15
> **nanbudh said:**
> I re ran the script without the t option and after the step where  it asked for localisation this is was the console output:
***************
Updating repositories list
<snip>
************************************************
So then  i ran apt-get update and it gave same output. whats happening?
Earlier when i had run the script with t option it had given a final message that latest firefox was installed. what happened now? Is this a problem with some packages not being found? I dont get it. Please help.

well, the error message says that you are missing the gpg key for the wine repository. from the wine website instructions ([http://www.winehq.org/site/download-deb)](http://www.winehq.org/site/download-deb)), you need to run the following command to add their gpg key to your apt:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
then, try running the script again, and this time it shouldn't error out. 

some explanation: when you ran the script earlier with '-t', it skipped the apt-get update step, because -t is just a dry-run test, so it doesn't actually do anything to modify your system (including apt-get update). but now that you are doing a live run, it's trying an apt-get update, and it failed because you didn't have the gpg key for the wine repository. so after you import the gpg key using the command above, you should be able to get through apt-get update without errors, and thus the script should complete. 

please give it a try - and report your results. :)

---

### Post by nanbudh on 2007-05-15
> **nanotube said:**
> well, the error message says that you are missing the gpg key for the wine repository. from the wine website instructions ([http://www.winehq.org/site/download-deb)](http://www.winehq.org/site/download-deb)), you need to run the following command to add their gpg key to your apt:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
then, try running the script again, and this time it shouldn't error out. 

some explanation: when you ran the script earlier with '-t', it skipped the apt-get update step, because -t is just a dry-run test, so it doesn't actually do anything to modify your system (including apt-get update). but now that you are doing a live run, it's trying an apt-get update, and it failed because you didn't have the gpg key for the wine repository. so after you import the gpg key using the command above, you should be able to get through apt-get update without errors, and thus the script should complete. 

please give it a try - and report your results. :)


Hi Nano! I tried the code you gave me and it gave the message OK. then i ran the installation script again. here is *end portion* of what it said in the console:
**********************
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found
Fetched 10B in 6s (1B/s)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

**********************
no downloading firefox. what do i do now my friend? is this all about updating 
agt-get?

---

### Post by nanotube on 2007-05-15
hey!
heh, looks like you have some third-party repositories that aren't getting updated. since your apt-get is all as updated as it can be at this point, i have made a new version of the script, just for you, that allows you to proceed even if repo updates failed. (well, it's not really just for you - your case is a valid indicator that i should enable a user to proceed even if repo updates aren't completely sucessful ;) )
it is attached to this message. try running it. 
when it says 'repo updates failed, would you like to proceed anyway' just say yes, and it should finish.

please report back the results. :)
and thanks for all your feedback and sticking with it. :)

---

### Post by sagepe on 2007-05-15
Hi there,

I've just run 3.2.0 of the firefox installer on my Dapper box; it ran with no problems and I'm currently running 2.0.0.3.  I'll give the thunderbird updater a try as soon as I can - might not be today though.

Nice script, I was going to do the updates manually but when I saw your request for testers I thought I'd pitch in.  Thanks for your efforts!

Regards,

Sagepe

---

### Post by nanotube on 2007-05-15
> **sagepe said:**
> Hi there,

I've just run 3.2.0 of the firefox installer on my Dapper box; it ran with no problems and I'm currently running 2.0.0.3.  I'll give the thunderbird updater a try as soon as I can - might not be today though.

Nice script, I was going to do the updates manually but when I saw your request for testers I thought I'd pitch in.  Thanks for your efforts!

Regards,

Sagepe

thanks you for your help! :)

---

### Post by coolcar on 2007-05-15
Hi Nanotube ( this time i get your name right )

I tried the Thunderbird script on my Dapper and it worked fine as well. Looks good ! :)

Cheers,

---

### Post by nanotube on 2007-05-15
> **coolcar said:**
> Hi Nanotube ( this time i get your name right )

I tried the Thunderbird script on my Dapper and it worked fine as well. Looks good ! :)

Cheers,

excellent, thanks! i will push this version out to the sf.net fileservers after nanbudh comes back and verifies that the apt-get update failure handler works. ;)

---

### Post by sagepe on 2007-05-15
> **nanotube said:**
> thanks you for your help! :)

No Problem.  I have since tested all my Firefox plugins and they have migrated properly.  I have also run the thunderbird script and have had no problems so far.  Obviously had to re-install enigmail from the standard add-on package as the debian/ubuntu version no longer integrates.

By the way, do you happen to know of a way to integrate 2.x with the GNOME notification area in Dapper?  The Extension I was using in 1.5 (New Mail Icon 1.2.2, see <http://moztraybiff.mozdev.org/>) isn't compatible with 2?

---

### Post by nanbudh on 2007-05-16
Hi,
I ll get back as soon as possible. and thanks so much for the effort.

---

### Post by nanbudh on 2007-05-16
Hi Nanotube,
I tried the new script you provided. but alas no success yet. here is the output:
*************************
Welcome to the Ubuntuzilla Firefox script version 3.3.0

This script installs the latest release of the official Mozilla build of Firefox  on Ubuntu Linux. If you run into any problems using this script, or have featur e requests, suggestions, or general comments, please visit our website at http:/ /pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla

The most recent release of firefox is detected to be 2.0.0.3. Please make sure t his is correct before proceeding. (You can confirm by going to [http://www.mozill](http://www.mozill) a.com/) Is it correct [y/n]? y
w3m: Can't load [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/l](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/l) inux-i686/.
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please c heck the help section of our website at [http://pykeylogger.sourceforge.net/wiki/](http://pykeylogger.sourceforge.net/wiki/) index.php/Ubuntuzilla for steps you can take to resolve this problem.]
Enter your choice of localization: 1
Your input is not in the range of available localizations. Please try again: 2
Your input is not in the range of available localizations. Please try again: 3
Your input is not in the range of available localizations. Please try again: 100
Your input is not in the range of available localizations. Please try again: 0
****************
I know from earlier that en-us choice was num 10. but whatever i enter the script does not like it.
seems we have a problem. BTW can this be something related to ubuntu version? i am running 6.06 dapper. and another thing, can this be something happeneing at regional level? i mean like my location and my ISP or something? And another point; the script froze at confirmation step for almost 7-10 mins before it started up again on the next step of giving the message regarding ftp.mozilla.org.
I tried the script thrice but got the same results.

---

### Post by nanotube on 2007-05-16
hmm, one problem on top of another
it seems that just today mozilla's ftp.mozilla.org mirror is down!
i will have to change the links to point to releases.mozilla.org instead, unless ftp.mozilla.org comes back up.
you can edit the script you have, and replace every instance of "ftp.mozilla.org" with "releases.mozilla.org", and try running it again...

edit: ftp.mozilla.org is back up, so you don't have to edit the script (unless you already have). just run it again, and it should work.

---

### Post by nanbudh on 2007-05-17
I ran the script after making the changes. and it took some time but new version of the firefox was finally installed. i am glad to have finally succeeded. All the credit of course goes to you.Thanks for the help and the programming u did.
A question: how is updating through this script different from updating through the Software Update message box that appears when i log in to my administrative account?Because i think firefox update was mentioned in the lest last time i checked. Though i did no go forward to update it.

---

### Post by nanotube on 2007-05-17
wohoo! :) nice! :)

as for updates - there is a section about updating on our website:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla)

updating through the built-in updater is basically the same as updating through running the script again another time. it just saves on the download, since the updater doesn't download the whole firefox, but just the patch to the next version. i guess it's better to use the "official" method if you can. :)

---

### Post by AaronMT on 2007-05-20
I am trying to install Thunderbird 2.0 on a new install of Ubuntu 7.04 but the script will hang before even showing the first prompt.

I control-c to abort the script, try again nothing. I tried a third time and I finally got the y/n prompt and install followed smooth as usual.

Just wanted to let you know.

---

### Post by nanotube on 2007-05-21
hi
thanks for your feedback :)
looks like it was having trouble accessing the mozilla.com website... 
i will put a shorter timeout on version retrieval, and show a "retrieving" message, in the next version.

---

