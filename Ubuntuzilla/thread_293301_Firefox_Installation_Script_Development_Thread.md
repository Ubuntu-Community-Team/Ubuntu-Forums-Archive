---
title: "Firefox Installation Script Development Thread"
date: 2006-05-08
forum: Ubuntuzilla
---

### Post by aysiu on 2006-05-08
**Introduction**
Starting with the second post in this thread, *nanotube* brought to life a sophisticated script translating the many copy-and-paste commands from the Ubuntu Wiki for getting the Mozilla (not Ubuntu) build of Firefox installed.

**News**
We now have a subforum in the Ubuntu Forums! You're in it right now.

---

### Post by nanotube on 2006-05-24
[QUOTE=aysiu]
For the future, you might want to know that I've created a script that automates the Wiki instructions:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)[/QUOTE]
by the way, i was looking at your script, and it lacks exit status checking in a big way. it just plods through the wiki instructions. so, for example, say, if the wget fails, it will just keep going on trying to untar, and that will fail, and it will try to do other stuff... in other words, not really smooth. you "should" check the exit status of the command before moving on to the next step.

---

### Post by aysiu on 2006-05-24
[QUOTE=nanotube]by the way, i was looking at your script, and it lacks exit status checking in a big way. it just plods through the wiki instructions. so, for example, say, if the wget fails, it will just keep going on trying to untar, and that will fail, and it will try to do other stuff... in other words, not really smooth. you "should" check the exit status of the command before moving on to the next step.[/QUOTE] I'm not a programmer, so I don't know how to do that.

The script is open source (after all, I just lifted it straight off the Wiki instructions). Go ahead and modify it as you see fit. I have no doubt that it can be improved--right now, though, it's the easiest way to get 1.5.0.3 on Breezy.

Ideally, it would have these exit things you're talking about. Ideally, it would ask the user what version of Firefox to get (British, American, etc.) and fetch that. Ideally, it would figure out if the mirror it's trying to pull from is dead and pull from another mirror instead.

Right now, though, the only other alternatives are:

Wiki (copy and paste a lot of instructions)
Automatix (install a whole new program and change up your sources.list--not a bad thing at all, but it's a bit more involved)
Upgrade Dapper (extremely involved, possibly resulting in a lot of breakage)

In other words, it's the best at what it does right now. If you want to make it better, I'm all for it!

---

### Post by nanotube on 2006-05-24
[QUOTE=aysiu]I'm not a programmer, so I don't know how to do that.

The script is open source (after all, I just lifted it straight off the Wiki instructions). Go ahead and modify it as you see fit. I have no doubt that it can be improved--right now, though, it's the easiest way to get 1.5.0.3 on Breezy.

Ideally, it would have these exit things you're talking about. Ideally, it would ask the user what version of Firefox to get (British, American, etc.) and fetch that. Ideally, it would figure out if the mirror it's trying to pull from is dead and pull from another mirror instead.

Right now, though, the only other alternatives are:

Wiki (copy and paste a lot of instructions)
Automatix (install a whole new program and change up your sources.list--not a bad thing at all, but it's a bit more involved)
Upgrade Dapper (extremely involved, possibly resulting in a lot of breakage)

In other words, it's the best at what it does right now. If you want to make it better, I'm all for it![/QUOTE]
heh ok, i will take a crack at it and see what comes out! :)

---

### Post by aysiu on 2006-05-24
[QUOTE=nanotube]heh ok, i will take a crack at it and see what comes out! :)[/QUOTE] Thanks.

I'm wondering how much demand there will be for it in a week, though.

Do you think people would be cool with Ubuntu's Firefox as long as they use the "take back the Firefox logo" script? Or would they, for some other reason, want the official Mozilla version anyway?

---

### Post by nanotube on 2006-05-24
[QUOTE=aysiu]Thanks.

I'm wondering how much demand there will be for it in a week, though.

Do you think people would be cool with Ubuntu's Firefox as long as they use the "take back the Firefox logo" script? Or would they, for some other reason, want the official Mozilla version anyway?[/QUOTE]

well, at some point in the future, i'm sure firefox 1.6 or 2.0 will come out, and just like ff15 on breezy now, it will be absent from the dapper repositories, and then everyone will be asking "how come i still have ff 1.5 when on mozilla.org it shows 2.0 is released? how do i install it?" and that's when interest in your firefox install script will be revived anew. :)

also, i am not sure, but if ubuntu makes some changes to the official ubuntu firefox, that makes automatic updates through firefox not work correctly, then there might still be reason to use "original" firefox.

and another thing - i, for one, would probably wait until 1 or 2 months have passed since the dapper release, so that most bugs have time to be ironed out. since i use ubuntu on my main workhorse computer, i would hate for anything untoward to ruin the show after an upgrade. i am sure there will be quite a few people thinking the same thing - so maybe there will be some use for ff1.5 install on breely for a few months yet.

so, at any rate, i figure i can use a bit of practice in my bash scripting, no matter what the future has in store for this firefox install script. :)

---

### Post by aysiu on 2006-05-24
[QUOTE=nanotube]so, at any rate, i figure i can use a bit of practice in my bash scripting, no matter what the future has in store for this firefox install script. :)[/QUOTE] Sounds like as good a reason as any other. Go for it!

---

### Post by nanotube on 2006-05-24
[QUOTE=aysiu]Sounds like as good a reason as any other. Go for it![/QUOTE]
well, i went for it. :) here is the result:
```
#!/bin/bash
check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully."
    exit 1
  fi
}

echo -e "Updating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

echo -e "\nBacking up old Firefox preferences\n"
cp -R ~/.mozilla ~/.mozilla_backup
check_exit_status

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox has been installed successfully."

exit
```

basically, all i did was create a check_exit_status function that checks if the previous command has completed successfully, and invoked it after every command that the script performs. 

i also changed your multiline echo-s to single-line commands, by shoving in explicit \n-s and using "echo -e" so that they are interpreted correctly.

feel free to post this on your website in replacement of your original script. (a credit to me would be appreciated. :) )

and another note of warning - since my firefox new version is already installed, i did not actually run the script to test it - so it "may" have some undetected typos.

---

### Post by aysiu on 2006-05-25
Thanks, nanotube.

I'm going to do some extensive testing on my test Ubuntu box before posting it.

I also want to see if my uninstall script will work with your revised install script, too.

---

### Post by nanotube on 2006-05-25
[QUOTE=aysiu]Thanks, nanotube.

I'm going to do some extensive testing on my test Ubuntu box before posting it.

I also want to see if my uninstall script will work with your revised install script, too.[/QUOTE]
ah, testing is good. especially before passing it on to a bunch of unsuspecting users :)

hm, the uninstall should work just as well, since no changes have been made to the "meat" of the install script. but i suppose it doesnt hurt to check...

---

### Post by nanotube on 2006-05-25
made another addition to the script - a verification of the gpg key for the firefox tarball. always good to check integrity of the download.

also added a -f flag to rm, for good measure.

anyway, here is the updated script:
```

#!/bin/bash
check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully."
    exit 1
  fi
}

echo -e "Updating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

echo -e "\nBacking up old Firefox preferences\n"
cp -R ~/.mozilla ~/.mozilla_backup
check_exit_status

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature\n"
gpg --verify firefox-1.5.0.3.tar.gz.asc firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-1.5.0.3.tar.gz firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox has been installed successfully."

exit

```

---

### Post by aysiu on 2006-05-25
Okay, I've got the first bug.

I tested it on a fresh Breezy Ubuntu, and it exits because it cannot backup the non-existent /home/username/.mozilla folder when it's trying to back up the existing profile.

Since it's a fresh install, there is no .mozilla folder. I don't think this should make the script stop. It should produce and error and then just keep proceeding.

Another thing--as far as I can tell, Breezy uses /usr/lib/mozilla-firefox/plugins for plugins, but Dapper uses /usr/lib/firefox/plugins.

So, if the script gets updated for Dapper, that line should be changed.

---

### Post by nanotube on 2006-05-25
hmm, ok, well, here is the new script, addressing both concerns:

```
#!/bin/bash
check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully."
    exit 1
  fi
}

if grep -q "Breezy" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "Dapper" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

echo -e "Updating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature\n"
gpg --verify firefox-1.5.0.3.tar.gz.asc firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-1.5.0.3.tar.gz firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox has been installed successfully."

exit
```

added a test for ubuntu version, which sets plugin directory accordingly, as well as a test for existence of ~/.mozilla before attempting to copy it (and proceeding if it doesn't exist).

---

### Post by aysiu on 2006-05-25
Whoa! Awesome response time! I'll test the new script out tonight.

The script is almost perfect, thanks to your hard work.

The next step to make it perfect would be to have it download the language version of choice and also pick a different mirror if the mirror it's trying to draw from is down.

That's a big next step, though.

Let me test out what you've written so far. More later...

---

### Post by nanotube on 2006-05-25
[QUOTE=aysiu]Whoa! Awesome response time! I'll test the new script out tonight.

The script is almost perfect, thanks to your hard work.

The next step to make it perfect would be to have it download the language version of choice and also pick a different mirror if the mirror it's trying to draw from is down.

That's a big next step, though.

Let me test out what you've written so far. More later...[/QUOTE]
hmm, well, the choice of language version should be fairly straightforward to code in. i will give it a crack tonight (or maybe tomorrow). so would the choosing of a different mirror in case of failure - if i had a list of mirrors. i kinda thought that the ftp-mozilla.netscape.com automatically passed through the requests to a bunch of mirrors, but maybe i'm wrong?

---

### Post by aysiu on 2006-05-25
[QUOTE=nanotube]hmm, well, the choice of language version should be fairly straightforward to code in. i will give it a crack tonight (or maybe tomorrow). so would the choosing of a different mirror in case of failure - if i had a list of mirrors. i kinda thought that the ftp-mozilla.netscape.com automatically passed through the requests to a bunch of mirrors, but maybe i'm wrong?[/QUOTE] You know, maybe you should host this--the new script you've created is way beyond me. I think once we finish testing it, you should put it up on your keylogger site, and I'll just link to it from Psychocats.

---

### Post by nanotube on 2006-05-25
[QUOTE=aysiu]You know, maybe you should host this--the new script you've created is way beyond me. I think once we finish testing it, you should put it up on your keylogger site, and I'll just link to it from Psychocats.[/QUOTE]

it's all the same to me. since you are doing the testing, and since you made the original script, you have just as much claim on this script as i do. so don't worry. ;)

oh and btw, so do you know about a list of official mirrors for firefox? i looked around on mozilla.org/com, and couldn't find it. only site i've seen is one we download from already...

---

### Post by aysiu on 2006-05-25
> **nanotube]it's all the same to me. since you are doing the testing, and since you made the original script, you have just as much claim on this script as i do. so don't worry.  said:**
>  That's very funny, nanotube.

I hardly have any claim to this script. "My" script is basically just ```
#!/bin/bash
``` with the Wiki instructions pasted in one after the other and a *wget* command.

Your script is a fully functional script that includes programming and syntax created by you.

While I would be able to modify my script (and I have) when people have told me about problems with it, your script is way beyond my editing capabilities, so it would be up to you to maintain--thus, it would make sense to host it on your site.

I will probably post up something like: > This script has been improved upon and moved. It now lives here [link to your site]. Here are the differences between the new script and the old script [list of changes]. If you still want to use the old script, for whatever strange reason, here it is [link to my script]. Otherwise, please use the new script [link to your script], which is smarter and will be updated as needed.

[quote]
oh and btw, so do you know about a list of official mirrors for firefox? i looked around on mozilla.org/com, and couldn't find it. only site i've seen is one we download from already... [http://www.mozilla.org/mirrors.html](http://www.mozilla.org/mirrors.html)

---

### Post by nanotube on 2006-05-25
[QUOTE=aysiu]That's very funny, nanotube.

I hardly have any claim to this script. "My" script is basically just ```
#!/bin/bash
``` with the Wiki instructions pasted in one after the other and a *wget* command.

Your script is a fully functional script that includes programming and syntax created by you.

While I would be able to modify my script (and I have) when people have told me about problems with it, your script is way beyond my editing capabilities, so it would be up to you to maintain--thus, it would make sense to host it on your site.
[/quote]
oh no, maintenance! what have i gotten myself into??? :mrgreen: :D 

still, i think you underplay your contribution - first, you had the initiative and the foresight to actually make a script out of it (i don't see anyone else who did). second, testing is nothing to scoff at, either (it's an important part of any piece of code). neither is #!/bin/bash. :)

> 
I will probably post up something like: ...

well if you insist, sure, that would be fine. i'd still appreciate your testing the script, before we post it up for "general consumption". :)

> 
 [http://www.mozilla.org/mirrors.html](http://www.mozilla.org/mirrors.html)
ah, thanks! i notice also that it says "Note: when you connect to ftp.mozilla.org, you are connecting to one of the United States mirrors."
so we will just change our wgets to go to ftp.mozilla.org, and all the mirroring will be taken care of by load balancing magic. a bunch of US mirrors ought to be good enough, methinks?

---

### Post by aysiu on 2006-05-25
[QUOTE=nanotube]oh no, maintenance! what have i gotten myself into??? :mrgreen: :D [/quote] I think that's a question we all ask ourselves sometimes.

> 
still, i think you underplay your contribution - first, you had the initiative and the foresight to actually make a script out of it (i don't see anyone else who did). second, testing is nothing to scoff at, either (it's an important part of any piece of code). neither is #!/bin/bash. :) Well, in all fairness, Automatix does install Firefox. I created the script because I wanted something a little less committal. If people had all the plugins they wanted and such, I didn't want to have to tell them "Install Automatix" just to get the latest Firefox, too.

As with the Add-On CD project (which seems to be in hibernation right now), I'm a big fan of the philosophy, "We need a good way to do X. But if no one is going to do X well, I'll do X terribly just so we'll have it!"

> 
well if you insist, sure, that would be fine. i'd still appreciate your testing the script, before we post it up for "general consumption". :) I'll do extensive testing in the next 24-hours. 

> 
ah, thanks! i notice also that it says "Note: when you connect to ftp.mozilla.org, you are connecting to one of the United States mirrors."
so we will just change our wgets to go to ftp.mozilla.org, and all the mirroring will be taken care of by load balancing magic. a bunch of US mirrors ought to be good enough, methinks? Cool. I guess you can hold off on the European ones for now. Or, if you get tired of maintaining the project, maybe someone else will take up the reins.

---

### Post by aysiu on 2006-05-25
I'm going to test this, which is basically your last script but using ftp.mozilla.org: ```
#!/bin/bash
check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully."
    exit 1
  fi
}

if grep -q "Breezy" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "Dapper" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

echo -e "Updating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature\n"
gpg --verify firefox-1.5.0.3.tar.gz.asc firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-1.5.0.3.tar.gz firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox has been installed successfully."

exit
```

---

### Post by nanotube on 2006-05-25
the one you posted is not the last - it is missing the gpg signature verification code, and the ubuntu version checking code. 
this would be the last one, with ftp.mozilla.org:

```
#!/bin/bash
check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully."
    exit 1
  fi
}

if grep -q "Breezy" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "Dapper" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

echo -e "Updating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature\n"
gpg --verify firefox-1.5.0.3.tar.gz.asc firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-1.5.0.3.tar.gz firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox has been installed successfully."

exit
```

edit: whoops, i guess you edited yours to reflect the newest code while i was typing my message here. :)

---

### Post by nanotube on 2006-05-25
[QUOTE=aysiu]
 I'll do extensive testing in the next 24-hours. 
[/quote]
cool, thanks.

> 
 Cool. I guess you can hold off on the European ones for now. Or, if you get tired of maintaining the project, maybe someone else will take up the reins.
well, i can always throw in a prompt that asks people that if they are in europe, they can select one of the european mirrors - do you think that would make a difference? i always figure, us mirrors should work for europeans just as well...

---

### Post by aysiu on 2006-05-25
[QUOTE=nanotube]cool, thanks.[/quote] Okay. I just tested it with a .mozilla folder and without one. It works!

Only two issues:

1. I'm not sure if this is because I'm using a VMWare Ubuntu right now, but my /etc/issue says: ```
Ubuntu 6.06 LTS \n \l
```, so the first time I tried to run it, I was told the script was for only Breezy or Dapper. So I modified my /etc/issue file, so I could test the rest of the script. Maybe one of the strings you could check for would also be *6.06* or *5.10*?

2. The first time I ran the script, the script stalled for a while at this part: ```
gpg: directory `/home/username/.gnupg' created
gpg: new configuration file `/home/username/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/username/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/username/.gnupg/secring.gpg' created
gpg: keyring `/home/username/.gnupg/pubring.gpg' created

``` The second time, it flew right through. It may be a good idea to create some kind of a warning to say "If this is your first time using this script, this may take a while--don't worry." I think I waited a good thirty seconds.

> 
well, i can always throw in a prompt that asks people that if they are in europe, they can select one of the european mirrors - do you think that would make a difference? i always figure, us mirrors should work for europeans just as well... I'm not sure if it's a mirror issue or if the British version of Firefox, for example, is different in some way (I don't know). I'm thinking of the part of the address that's en-US as opposed to en-GB or whatever else it could be.

---

### Post by nanotube on 2006-05-25
[QUOTE=aysiu]Okay. I just tested it with a .mozilla folder and without one. It works!

Only two issues:

1. I'm not sure if this is because I'm using a VMWare Ubuntu right now, but my /etc/issue says: ```
Ubuntu 6.06 LTS \n \l
```, so the first time I tried to run it, I was told the script was for only Breezy or Dapper. So I modified my /etc/issue file, so I could test the rest of the script. Maybe one of the strings you could check for would also be *6.06* or *5.10*?
[/quote]
ah hmm, i guess its not "dapper" until it is released :) i suppose checking for the version number would be more portable, so we will do that, instead.

> 
2. The first time I ran the script, the script stalled for a while at this part: ```
gpg: directory `/home/username/.gnupg' created
gpg: new configuration file `/home/username/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/username/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/username/.gnupg/secring.gpg' created
gpg: keyring `/home/username/.gnupg/pubring.gpg' created

``` The second time, it flew right through. It may be a good idea to create some kind of a warning to say "If this is your first time using this script, this may take a while--don't worry." I think I waited a good thirty seconds.

ah well yea, it had to create some keypairs, i suppose. ok, we will make that note. 

> 
 I'm not sure if it's a mirror issue or if the British version of Firefox, for example, is different in some way (I don't know). I'm thinking of the part of the address that's en-US as opposed to en-GB or whatever else it could be.

well, the en-US vs en-GB part is the localization, an issue that is separate from the mirroring issue, because the entire directory tree is mirrored on all mirrors, so any localized version can be gotten from any mirror. and yes, i am planning on offering the user a choice of localization for the download, as well (as we mentioned some post ago).

thanks for the testing, those are some issues that one certainly wouldn't pick up without actually running the whole script on a fresh machine :)

---

### Post by aysiu on 2006-05-25
I have yet to test it on a Breezy box, but I'll do that later. If I test it on Breezy, and it's good, do you want to go ahead and post it on your keylogger site and give me the link?

---

### Post by nanotube on 2006-05-25
[QUOTE=aysiu]I have yet to test it on a Breezy box, but I'll do that later. If I test it on Breezy, and it's good, do you want to go ahead and post it on your keylogger site and give me the link?[/QUOTE]

sure, will do.
in the meantime, here is the "newest" version of the script, with the extra warning message about gpg, and usage of version numbers rather than version names. pretty minor changes, but just for the record:

```
#!/bin/bash
check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.3/linux-i686/en-US/firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature\n"
gpg --verify firefox-1.5.0.3.tar.gz.asc firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-1.5.0.3.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-1.5.0.3.tar.gz firefox-1.5.0.3.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox has been installed successfully."

exit
```

---

### Post by nanotube on 2006-05-25
just let me know when you are done testing on breezy, and i will throw it up on my site. :)

---

### Post by aysiu on 2006-05-25
It works on Breezy! Congratulations!

The signature thing didn't take long *and* I didn't get this warning: > Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior Does that mean your script detects whether or not the system has used gpg before? I'm not sure whether my Breezy installation has used it before or not.

This might be a little disconcerting to a new user, though: ```
Importing Mozilla Software Releases public key

gpg: directory `/home/username/.gnupg' created
gpg: new configuration file `/home/username/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/username/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/username/.gnupg/secring.gpg' created
gpg: keyring `/home/username/.gnupg/pubring.gpg' created
gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: /home/username/.gnupg/trustdb.gpg: trustdb created
gpg: key 0E3606D9: public key "Mozilla Software Releases <releases@mozilla.org>" imported
gpg: **no ultimately trusted keys found**
gpg: Total number processed: 1
gpg:               imported: 1

Verifying signature

gpg: Signature made Tue 02 May 2006 02:39:47 AM PDT using DSA key ID 1AF32821
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: [b]WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.[/b]
Primary key fingerprint: F57F 372A 8C6D 4F55 72DE  C9B9 696E 3431 0E36 06D9
     Subkey fingerprint: 22D5 FEAF D70A 8E29 E999  4ABC C660 CCE2 1AF3 2821
``` Is that normal?

---

### Post by nanotube on 2006-05-25
don't know why you didnt get that warning.. are you sure you used the version of the script that had it? it is a simple echo statement, that gets executed all the time, so if it was there, you /should/ have gotten it.

as to the key being "not trusted", that is all normal - you have to jump through a bunch of hoops to convince gpg that a key is actually trusted. :)

---

### Post by aysiu on 2006-05-25
[QUOTE=nanotube]don't know why you didnt get that warning.. are you sure you used the version of the script that had it? it is a simple echo statement, that gets executed all the time, so if it was there, you /should/ have gotten it.[/quote] I'm sorry--the warning did appear--it just appeared a lot earlier, so I didn't notice it. It's weird that it didn't pause for a long time on this go-round, though.

> 
as to the key being "not trusted", that is all normal - you have to jump through a bunch of hoops to convince gpg that a key is actually trusted. :) Maybe another echo statement just telling people not to worry if they see "not trusted"? I know it sounds like a lot of warnings, but that could definitely freak people out...

---

### Post by nanotube on 2006-05-25
hmm, well, here is a link to the new install firefox section on my site:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)
the direct link to the script is
[http://pykeylogger.sourceforge.net/installnewfirefox.sh](http://pykeylogger.sourceforge.net/installnewfirefox.sh)

(extra message about untrusted keys added)

so, for the "near future", i am thinking we need to add the following:
- user selection of localization
- autoselection of latest firefox version (so i dont have to update the script every time a new firefox update comes out.

am i forgetting anything else?

---

### Post by aysiu on 2006-05-25
[QUOTE=nanotube]hmm, well, here is a link to the new install firefox section on my site:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)
the direct link to the script is
[http://pykeylogger.sourceforge.net/installnewfirefox.sh](http://pykeylogger.sourceforge.net/installnewfirefox.sh)

(extra message about untrusted keys added)[/quote] Thanks, nanotube. I've updated my page to link to yours. I may still point people to my page just because the URL is easier to remember--I don't think they'll mind the extra click to get to yours.

I also appreciate the acknowledgement, but it's not really necessary, since you did most of the hard work.

Maybe you can thank me for testing in the comments of the script instead of mentioning me on the main page?

> 
so, for the "near future", i am thinking we need to add the following:
- user selection of localization
- autoselection of latest firefox version (so i dont have to update the script every time a new firefox update comes out.

am i forgetting anything else? That sounds like that's about it. Congratulations for making such a great script! I'll definitely be here to help test future versions.

---

### Post by handy on 2006-05-26
What a pleasant interaction **aysiu & nanotube**.

I really enjoyed the read!

You 2 work really well together.

Thanks! :KS

---

### Post by jared85 on 2006-05-26
aysiu & nanotube I commend you both!

Splendid job on the install script. I used it and everything went as smooth as possible!

Thanks for making things so easy :) 

cheers to  you both!

---

### Post by aysiu on 2006-05-26
In all fairness, nanotube did the bulk of the hard work.

All I did was run the script a few times and write back, "It worked!"

---

### Post by nanotube on 2006-05-26
> **aysiu]Thanks, nanotube. I've updated my page to link to yours. I may still point people to my page just because the URL is easier to remember--I don't think they'll mind the extra click to get to yours.
[/quote]
no problem, sounds good :)

> 
I also appreciate the acknowledgement, but it's not really necessary, since you did most of the hard work.

Maybe you can thank me for testing in the comments of the script instead of mentioning me on the main page?

i give you the credit that i think you are due. so unless you have strong objections or something, i'd prefer to keep it the way it is.  said:**
> 
 That sounds like that's about it. Congratulations for making such a great script! I'll definitely be here to help test future versions.
excellent :). there will certainly be future versions - especially once i am done with my stats comp exam.

---

### Post by nanotube on 2006-05-26
[QUOTE=aysiu]In all fairness, nanotube did the bulk of the hard work.

All I did was run the script a few times and write back, "It worked!"[/QUOTE]
you also made a lot of good suggestions, had the initial idea to make the script in the first place, and served as a motivator for me to work on it. we made a good team, i'd say. ;)

---

### Post by aysiu on 2006-05-26
We make a good team. I just don't want people to think I wrote that script. Motivator? Okay. Tester? Also okay. I do still believe you did all the hard work, though.

---

### Post by nanotube on 2006-05-26
[QUOTE=aysiu]We make a good team. I just don't want people to think I wrote that script. Motivator? Okay. Tester? Also okay. I do still believe you did all the hard work, though.[/QUOTE]
heh, well, this must be a rare sight - people trying to give credit to each other over the other's objection :)

i think "in collaboration with" is sufficiently vague to be acceptable under your strict criteria - it does not say "aysiu wrote half the script", it just says that we collaborated while writing it, without specifying the nature of the contribution of either party. but if you would prefer, i can say "in collaboration with aysiu, who helped with testing, ideas, and motivation." would that make you happier? :)

---

### Post by aysiu on 2006-05-26
[QUOTE=nanotube]heh, well, this must be a rare sight - people trying to give credit to each other over the other's objection :)

i think "in collaboration with" is sufficiently vague to be acceptable under your strict criteria - it does not say "aysiu wrote half the script", it just says that we collaborated while writing it, without specifying the nature of the contribution of either party. but if you would prefer, i can say "in collaboration with aysiu, who helped with testing, ideas, and motivation." would that make you happier? :)[/QUOTE] I can agree on that. Yes, that would make me happier. We finally agree!

I'm just being silly, I guess, but thanks for indulging me.

---

### Post by handy on 2006-05-26
Just point people to this thread, if you want them to know who did what!! :KS 

Great Stuff!!

---

### Post by nanotube on 2006-05-28
[QUOTE=aysiu]I can agree on that. Yes, that would make me happier. We finally agree!

I'm just being silly, I guess, but thanks for indulging me.[/QUOTE]
:D it is done.

---

### Post by nanotube on 2006-05-28
hey aysiu,
please test the new version of the script, when you have a chance. i will upload it to the site once i have your testing results :)
it automatically pulls the newest version, and the available localizations for it, off the mozilla servers, and lets user choose localization.
here is the new and improved script:

```

#!/bin/bash
#
# Script to automatically download and install the newest firefox version for linux, on an Ubuntu system.
# Requires an internet connection to work (obviously).
# 
# Version 1.5, May 28, 2006

#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest firefox release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com |grep "product=" -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of firefox is detected to be $VERSION. Please make sure this is correct before proceeding. Is it correct [y/n]? "
read ans
case $ans in
     Y|y) ;;
[Yy][Ee][Ss]) ;;
     N|n) exit ;;
[Nn][Oo]) exit ;;
       *) echo "Invalid command"; exit;;
esac

## Get available localizations
LOCALIZATIONS=( `wget -q -O - http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/ | grep 'img src="/icons/folder.gif"' | grep -v "xpi" | sed -e 's/<img.*href="//' | sed -e 's@/">.*@@'` )
# for i in $TEST; do echo $i; done

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for firefox. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))  # Double parentheses, and "LIMIT" with no "$".
do
  echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  fi
  if [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
read ans
case $ans in
     Y|y) ;;
[Yy][Ee][Ss]) ;;
     N|n) exit ;;
[Nn][Oo]) exit ;;
       *) echo "Invalid command"; exit;;
esac


echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
gpg --verify firefox-$VERSION.tar.gz.asc firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox version $VERSION has been installed successfully."

exit

```

edit: added more input checking on the localizations choice.

---

### Post by aysiu on 2006-05-29
Sounds awesome! You work very quickly.

How will I know if it's pulling the latest version... ? We probably won't be able to do full testing on that until 1.5.0.4 or 2.0 comes out.

But I can test the choice of locale. When I'm done testing, I'll post back to this thread to let you know.

---

### Post by nanotube on 2006-05-29
[QUOTE=aysiu]Sounds awesome! You work very quickly.

How will I know if it's pulling the latest version... ? We probably won't be able to do full testing on that until 1.5.0.4 or 2.0 comes out.

But I can test the choice of locale. When I'm done testing, I'll post back to this thread to let you know.[/QUOTE]

heh well, you will know because if you look at the script, and search for "1.5.0.3", you won't find it hard coded anywhere - because it is getting the info from the website. so if it does in fact download 1.5.0.3, then you will know it works - because otherwise it wouldn't know what to get. :)

edit: and another note on the testing: try inputting a bunch of 'bad' stuff when it asks you things, and make sure that it doesn't get by input checking.

---

### Post by aysiu on 2006-05-29
[QUOTE=nanotube]heh well, you will know because if you look at the script, and search for "1.5.0.3", you won't find it hard coded anywhere - because it is getting the info from the website. so if it does in fact download 1.5.0.3, then you will know it works - because otherwise it wouldn't know what to get. :)

edit: and another note on the testing: try inputting a bunch of 'bad' stuff when it asks you things, and make sure that it doesn't get by input checking.[/QUOTE] I'll report back after I try the bad stuff, but I'll tell you right now that it *did* detect 1.5.0.3 as the latest, and if you select English and American as the locale, then it works.

---

### Post by nanotube on 2006-05-29
[QUOTE=aysiu]I'll report back after I try the bad stuff, but I'll tell you right now that it *did* detect 1.5.0.3 as the latest, and if you select English and American as the locale, then it works.[/QUOTE]
cool :) try installing like a spanish version (or whatever other language you may be at least passingly familiar with), and see if that gets the spanish firefox up, too.

---

### Post by aysiu on 2006-05-29
[QUOTE=nanotube]cool :) try installing like a spanish version (or whatever other language you may be at least passingly familiar with), and see if that gets the spanish firefox up, too.[/QUOTE] It works, even with Spanish.

I tried to say "no" to 1.5.0.3 being the latest version, and it quit. I think that's okay. Ideally (maybe for the next version of the script), it would offer some way (an email or web address) where the problem can be reported back to you.

I tried to type gibberish in answer to the same question and I got that it was an invalid command, and then it quit... which, again, is not a terrible thing, but ideally it would tell you "Yeah, your answer needs to be yes or no. Try again."

Incidentally, when I typed gibberish for the locale, I did get such a response, so that's working ideally.

Congratulations! Your latest revision works!

---

### Post by nanotube on 2006-05-29
hey
ok, you are right, it should be more graceful when asking for yes/no answers instead of just quitting. here is the new version, that addresses all your suggestions (and thank you very much for those, by the way):

```

#!/bin/bash
#
# installnewfirefox.sh
#               Script to automatically download and install the newest firefox version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installnewfirefox.sh  1.6  29-May-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest firefox release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com |grep "product=" -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of firefox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
LOCALIZATIONS=( `wget -q -O - http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/ | grep 'img src="/icons/folder.gif"' | grep -v "xpi" | sed -e 's/<img.*href="//' | sed -e 's@/">.*@@'` )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for firefox. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  fi
  if [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install firefox.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
gpg --verify firefox-$VERSION.tar.gz.asc firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox version $VERSION has been installed successfully."

exit

```

please give it a round or two of testing with invalid inputs and "no"s. (only things i changed were in the user interaction part, so you dont have to let it go through the entire install sequence if you want to save time).

---

### Post by aysiu on 2006-05-29
The revision works flawlessly.

---

### Post by nanotube on 2006-05-29
[QUOTE=aysiu]The revision works flawlessly.[/QUOTE]
great! thanks for all your help :)

---

### Post by nanotube on 2006-05-29
for the record, here is the newest version of the script (i also corrected the error that it would spit out because it couldn't handle empty input for localization choice correctly. 

```

#!/bin/bash
#
# installnewfirefox.sh
#               Script to automatically download and install the newest firefox version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installnewfirefox.sh  1.6  29-May-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest firefox release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com |grep "product=" -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of firefox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
LOCALIZATIONS=( `wget -q -O - http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/ | grep 'img src="/icons/folder.gif"' | grep -v "xpi" | sed -e 's/<img.*href="//' | sed -e 's@/">.*@@'` )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for firefox. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install firefox.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
gpg --verify firefox-$VERSION.tar.gz.asc firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox version $VERSION has been installed successfully."

exit

```

---

### Post by aysiu on 2006-05-29
Do you want this tested, or are you just posting it, as you said, "for the record"?

---

### Post by nanotube on 2006-05-29
[QUOTE=aysiu]Do you want this tested, or are you just posting it, as you said, "for the record"?[/QUOTE]
yea, just for the record. i already tested the "empty input" scenario. ;)

---

### Post by aysiu on 2006-05-29
By the way, you seem to be a programmer (correct me if I'm wrong). Is this how programming works in the "real" world? You start with a simple script and just keep adding improvements and testing them?

---

### Post by nanotube on 2006-05-30
[QUOTE=aysiu]By the way, you seem to be a programmer (correct me if I'm wrong). Is this how programming works in the "real" world? You start with a simple script and just keep adding improvements and testing them?[/QUOTE]
heh well, as it happens, i am not "a programmer" although i "can program" somewhat. :) but i do hang out with some programmers, and i read stuff about programming because it interests me, and i have also worked as a linux sysadmin for a few years, so i think i can answer your question with a modicum of thuthfulness. (but at this point i am a grad student in finance, so... no, i am not a programmer, or a even sysadmin, at the present time.)

and the answer is, it depends. :) if you are working on a  **commercial** software development project, where the end deliverable is a working piece of software, then this is not the way it works. painting the very broad-brush picture, first you make a more or less detailed plan, which says what kind of stuff your software will do, then you make the basic skeleton framework, and then you add features and flesh it out until your plan is fulfilled.

if you are working in system (or database) administration, though, where your goal is not to deliver a piece of software, but just to automate some parts of your, or others', job, (in other words, the program/script is a means to an end, rather than the end in itself) then yes, this is the way it works. first you make something basic, then you say oh, wouldn't it be nice if it also did that and add it in, and so on. 

and yet another if - if you are talking about FOSS software projects, then yes, unlike commercial projects, they do tend to be a "scratch an itch" type of deal, where the programmer first writes something simple, and then it just grows as features are added, etc. you can see a lot of actual examples of this happening if you just read some of the "project of the month" interviews on sourceforge :)

so to sum up, in the "real world" of system administration, this is the way it tends to work, in the "real world" of FOSS development, this is also the way it tends to work, but in the "real world" of commercial software development, it is not, or at least should not be, the way it works. 

and of course, if any actual programmers read this thread, they can feel free to disagree if i am wrong ;)

---

### Post by aysiu on 2006-05-30
Nanotube, thanks for the explanation. That makes sense.

---

### Post by drpaul on 2006-05-30
Don't know if you interested in other experiences, but here goes.

I have the Ubuntu FF installed normally.  I have the Mozilla 1.5.0.3 installed in /opt, but have to run it with sudo/gksudo for it to work. I decided to try your script [copied out of the latest (I think) code window].  My sources file has some added stuff to get non-Ubuntu apps, and the script didn't get far. I don't think that the errors encountered are really relevent to the FF install issue, but then, I don't really know.

```
paul@paulsbox:~$ ./ffupdate.sh
The most recent release of firefox is detected to be 1.5.0.3. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? y
Please choose the localization (language) for firefox. Enter the number of your choice from the list below.
0: ar
1: bg
2: ca
3: cs
4: da
5: de
6: el
7: en-GB
8: en-US
9: es-AR
10: es-ES
11: eu
12: fi
13: fr
14: ga-IE
15: gu-IN
16: he
17: hu
18: it
19: ja
20: ko
21: mk
22: nb-NO
23: nl
24: pa-IN
25: pl
26: pt-BR
27: ro
28: ru
29: sk
30: sl
31: sv-SE
32: tr
33: zh-CN
34: zh-TW
Enter your choice of localization: 8
You have chosen localization "en-US". Is that correct [y/n]? y

Updating repositories list

Password:
Ign http://wine.sourceforge.net binary/ Release.gpg
Hit http://wine.sourceforge.net binary/ Release
Get:1 http://kubuntu.org breezy Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://people.ubuntu.com ./ Release.gpg
Ign http://theli.free.fr ./ Release.gpg
Hit http://kubuntu.org breezy Release
Get:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Get:6 http://security.ubuntu.com breezy-security Release [27.0kB]
Ign http://deb.opera.com etch Release.gpg
Hit http://archive.ubuntu.com breezy Release
Ign http://people.ubuntu.com ./ Release
Ign http://theli.free.fr ./ Release
Get:7 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Ign http://deb.opera.com etch Release
Ign http://people.ubuntu.com ./ Packages
Get:8 ftp://ftp.free.fr breezy Release.gpg
Hit http://people.ubuntu.com ./ Packages
Ign http://koti.mbnet.fi breezy/ Release.gpg
Ign http://deb.opera.com etch/non-free Packages
Hit http://kubuntu.org breezy/main Packages
Ign http://theli.free.fr ./ Packages
Get:9 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Ign ftp://ftp.free.fr breezy Release.gpg
Hit http://deb.opera.com etch/non-free Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Err http://theli.free.fr ./ Packages
  404 Not Found
Ign http://koti.mbnet.fi breezy/ Release
Get:10 ftp://ftp.free.fr breezy Release
Get:11 http://security.ubuntu.com breezy-security/main Packages [62.8kB]
Get:12 http://archive.ubuntu.com breezy-updates/main Packages [39.0kB]
Ign http://koti.mbnet.fi breezy/ Packages
Ign ftp://ftp.free.fr breezy Release
Get:13 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:14 http://archive.ubuntu.com breezy-updates/main Sources [18.6kB]
Get:15 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:16 http://archive.ubuntu.com breezy-backports/main Packages [14.0kB]
Ign http://koti.mbnet.fi breezy/ Sources
Get:17 ftp://ftp.free.fr breezy/free Packages
Get:18 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:19 http://security.ubuntu.com breezy-security/main Sources [17.7kB]
Get:20 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:21 http://archive.ubuntu.com breezy-backports/universe Packages [26.1kB]
Get:22 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Get:23 http://archive.ubuntu.com breezy-backports/multiverse Packages [1353B]
Err http://koti.mbnet.fi breezy/ Packages
  404 Not Found
Ign ftp://ftp.free.fr breezy/free Packages
Get:24 http://security.ubuntu.com breezy-security/universe Packages [35.7kB]
Get:25 ftp://ftp.free.fr breezy/non-free Packages
Get:26 http://security.ubuntu.com breezy-security/universe Sources [5007B]
Ign http://wine.sourceforge.net binary/ Packages
Err http://koti.mbnet.fi breezy/ Sources
  404 Not Found
Hit http://wine.sourceforge.net binary/ Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:27 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:28 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Fetched 304kB in 6s (48.3kB/s)
Failed to fetch http://theli.free.fr/packages/breezy/./Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
Previous command did not complete successfully. Exiting.
paul@paulsbox:~$

```

[I tried to do a code box but ?????]

What do you think the problem is?

Paul

---

### Post by aysiu on 2006-05-30
```
Failed to fetch http://theli.free.fr/packages/breezy/./Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz  404 Not Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz  404 Not Found
Reading package lists... Done
``` These repositories are dead. Remove them from your sources.list.

---

### Post by drpaul on 2006-05-30
Thanks for the feedback. I fixed the sources.list file and now it gets to signature verification ending with 

```

13:25:48 (7.39 MB/s) - `firefox-1.5.0.3.tar.gz.asc' saved [186/186]


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.
gpg --keyserver subkeys.pgp.net --recv 1AF32821

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Tue 02 May 2006 03:39:47 AM MDT using DSA key ID 1AF32821
gpg: Can't check signature: public key not found
Previous command did not complete successfully. Exiting.
```

Looking in Synaptic I have gnupg installed. there are lots of other packages referring to gpg, but I don't know if this is the problem.

Looking for help again.

Paul

---

### Post by nanotube on 2006-05-30
hi, i just checked my script
and noticed that somehow a newline got deleted, no the gpg "get key" command was not actually running, but just getting displayed. 
i am going to update the script up on the website, go and re-download it again, and run it (but currently the sf.net shell server seems to be down).
in the meantime, here, copy and paste this into a text file, chmod to executable, and run:

```

#!/bin/bash
#
# installnewfirefox.sh
#               Script to automatically download and install the newest firefox version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installnewfirefox.sh  1.6  29-May-2006  nanotube@users.sf.net
# 
#
#######

check_exit_status () {
  if [ $? -ne 0 ]; then
    echo "Previous command did not complete successfully. Exiting."
    exit 1
  fi
}

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy or Dapper."
  exit 1
fi

## Get the newest firefox release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com |grep "product=" -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of firefox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
  [Nn][Oo]) echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
LOCALIZATIONS=( `wget -q -O - http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/ | grep 'img src="/icons/folder.gif"' | grep -v "xpi" | sed -e 's/<img.*href="//' | sed -e 's@/">.*@@'` )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for firefox. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
       Y|y) break ;;
  [Yy][Ee][Ss]) break ;;
       N|n) echo "In that case, start over by running this script again."; exit ;;
  [Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install firefox.

echo -e "\nUpdating repositories list\n"
sudo apt-get update
check_exit_status

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo apt-get -y install firefox libstdc++5
check_exit_status

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup
  check_exit_status
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd
check_exit_status

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nDownloading Firefox signature from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nImporting Mozilla Software Releases public key\n"
echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there will be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
gpg --keyserver subkeys.pgp.net --recv 1AF32821
check_exit_status

echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
gpg --verify firefox-$VERSION.tar.gz.asc firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -x -z -v -f firefox-$VERSION.tar.gz
check_exit_status

echo -e "\nRemoving the unzipped .tar.gz\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc
check_exit_status

echo -e "\nLinking plugins\n"
cd /opt/firefox/plugins/
sudo ln -s $PLUGINPATH/* .
check_exit_status

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
check_exit_status
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
check_exit_status
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
check_exit_status

echo -e "\nThe new Firefox version $VERSION has been installed successfully."

exit

```

---

### Post by drpaul on 2006-05-30
Final report:

It failed once again because there were existing link files in the /opt/... plugin directory. I removed them, and everything went to completion. FF now comes up 1.5.0.3!!!!

Don't know how compicated it would be to check to see if the file to be downloaded already exists. That might save someone with a slow link a lot of time if he were working through problems.

Thanks for the great script.

Paul

---

### Post by nanotube on 2006-05-30
[QUOTE=drpaul]Final report:

It failed once again because there were existing link files in the /opt/... plugin directory. I removed them, and everything went to completion. FF now comes up 1.5.0.3!!!!
[/quote]
just wondering... if the previous attempt interrupted at checking of signature, how come there were files in /opt. checking signature comes before unzipping stuff to /opt. was it because of an earlier installation, maybe?

> 
Don't know how compicated it would be to check to see if the file to be downloaded already exists. That might save someone with a slow link a lot of time if he were working through problems.

that is already being done, since we use "wget -c", where -c is "continue". if file already exists, it will exit without downloading anything again. if incomplete file exists,it will continue where it left off. 

> 
Thanks for the great script.

you are welcome :)

---

### Post by drpaul on 2006-05-30
NANOTUBE:
Yes, failure was due to an earlier install in /opt.

Thanks, again. This should be most useful since 1.5.0.3 is do much faster than 1.0.8.

Paul

---

### Post by nanotube on 2006-05-31
hey aysiu,
while the sourceforge shell servers are unreachable, i cannot change the script that's up there, so i changed the links to my university account.
so if you could change your psychocats direct link to point there too, that would probably be helpful for people. (or you can just remove the direct link, and let them come to my wiki page, which will in turn direct them to the correct script link.

and ps: drpaul, i'm glad it worked out :)

---

### Post by georgevn on 2006-05-31
is there something wrong with the firefox package, i couldn't see the list, so how can i choose the language?
> ~/Desktop$ ./installnewfirefox.sh
The most recent release of firefox is detected to be . Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? Y
Please choose the localization (language) for firefox. Enter the number of your choice from the list below.
Enter your choice of localization:
Please enter the number of your choice from the list: 1
Your input is not in the range of available localizations. Please try again: 2
Your input is not in the range of available localizations. Please try again:
[1]+  Stopped                 ./installnewfirefox.sh

---

### Post by nanotube on 2006-05-31
[QUOTE=georgevn]is there something wrong with the firefox package, i couldn't see the list, so how can i choose the language?[/QUOTE]
looks like for some reason it couldn't retrieve anything from the web.... were you connected to the net at the time? were you using the newest version of the script? (newest version can be found here: [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) )

---

### Post by aysiu on 2006-06-01
By the way, I just did a clean reinstall of Dapper and ran your Firefox script (the Thunderbird one worked excellently). I accidentally typed in the wrong locale. When it asked, "Is this the one you want?" and I said "No," the script just quit.

Is there any way you can make it so that it says, "Try again"?

---

### Post by joergenlie on 2006-06-01
[QUOTE=aysiu]Sure. ```
#!/bin/bash
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm /usr/bin/mozilla-firefox
sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox
cd
mv .mozilla .mozilla-1.5
mv .mozilla.ubuntu .mozilla
sudo rm -r /opt/firefox
``` Save that code as a text file called *removefirefox.sh* and save that to your desktop. Then ```
cd ~/Desktop
chmod +x removefirefox.sh
./removefirefox.sh
```[/QUOTE]

Well I tried this, but now I dont have any firefox at all. I have it installed but it wont start. says: usr/bin/firefox no such file or directory. I have tried to re-install firefox thru apt but it still wont work. Anyone with this problem, please help. Anyway just upgraded to dapper and it`s just smooth!!

Jørgen Norway

---

### Post by nanotube on 2006-06-01
[QUOTE=joergenlie]Well I tried this, but now I dont have any firefox at all. I have it installed but it wont start. says: usr/bin/firefox no such file or directory. I have tried to re-install firefox thru apt but it still wont work. Anyone with this problem, please help. Anyway just upgraded to dapper and it`s just smooth!!

Jørgen Norway[/QUOTE]
interesting... try running command
```
dpkg-divert --list
```
and see if anything about firefox comes up.
(post output here)

---

### Post by joergenlie on 2006-06-01
here it is :
joergenlie@ubuntu:~$ dpkg-divert --list
diversion of /sbin/depmod to /sbin/depmod.modutils by module-init-tools
diversion of /usr/share/man/man8/depmod.8.gz to /usr/share/man/man8/depmod.modutils.8.gz by module-init-tools
diversion of /usr/share/man/fr/man8/depmod.8.gz to /usr/share/man/fr/man8/depmod.modutils.8.gz by module-init-tools
diversion of /sbin/insmod to /sbin/insmod.modutils by module-init-tools
diversion of /usr/share/man/man8/insmod.8.gz to /usr/share/man/man8/insmod.modutils.8.gz by module-init-tools
diversion of /usr/share/man/fr/man8/insmod.8.gz to /usr/share/man/fr/man8/insmod.modutils.8.gz by module-init-tools
diversion of /sbin/update-modules to /sbin/update-modules.modutils by module-init-tools
diversion of /usr/share/man/man8/update-modules.8.gz to /usr/share/man/man8/update-modules.modutils.8.gz by module-init-tools
diversion of /usr/share/man/fr/man8/update-modules.8.gz to /usr/share/man/fr/man8/update-modules.modutils.8.gz by module-init-tools
diversion of /sbin/modinfo to /sbin/modinfo.modutils by module-init-tools
diversion of /usr/share/man/man8/modinfo.8.gz to /usr/share/man/man8/modinfo.modutils.8.gz by module-init-tools
diversion of /usr/share/man/fr/man8/modinfo.8.gz to /usr/share/man/fr/man8/modinfo.modutils.8.gz by module-init-tools
diversion of /sbin/kallsyms to /sbin/kallsyms.modutils by module-init-tools
diversion of /sbin/ksyms to /sbin/ksyms.modutils by module-init-tools
diversion of /sbin/lsmod to /sbin/lsmod.Lmodutils by module-init-tools
diversion of /usr/share/man/man8/lsmod.8.gz to /usr/share/man/man8/lsmod.modutils.8.gz by module-init-tools
diversion of /usr/share/man/fr/man8/lsmod.8.gz to /usr/share/man/fr/man8/lsmod.modutils.8.gz by module-init-tools
diversion of /sbin/modprobe to /sbin/modprobe.Lmodutils by module-init-tools
diversion of /usr/share/man/man8/modprobe.8.gz to /usr/share/man/man8/modprobe.modutils.8.gz by module-init-tools
diversion of /usr/share/man/fr/man8/modprobe.8.gz to /usr/share/man/fr/man8/modprobe.modutils.8.gz by module-init-tools
diversion of /sbin/rmmod to /sbin/rmmod.Lmodutils by module-init-tools
diversion of /usr/share/man/man8/rmmod.8.gz to /usr/share/man/man8/rmmod.modutils.8.gz by module-init-tools
diversion of /usr/share/man/fr/man8/rmmod.8.gz to /usr/share/man/fr/man8/rmmod.modutils.8.gz by module-init-tools
diversion of /usr/share/man/man5/modules.5.gz to /usr/share/man/man5/modules.modutils.5.gz by module-init-tools
diversion of /usr/share/man/fr/man5/modules.5.gz to /usr/share/man/fr/man5/modules.modutils.5.gz by module-init-tools
diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule
diversion of /usr/share/man/man1/ed2k.1.gz to /usr/share/man/man1/ed2k.xmule.1.gz by amule
diversion of /usr/bin/locate to /usr/bin/locate.notslocate by slocate
diversion of /usr/bin/updatedb to /usr/bin/updatedb.notslocate by slocate
diversion of /usr/share/man/man1/locate.1.gz to /usr/share/man/man1/locate.notslocate.1.gz by slocate
diversion of /usr/share/man/man1/updatedb.1.gz to /usr/share/man/man1/updatedb.notslocate.1.gz by slocate
diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate
diversion of /usr/lib/gimp/2.0/plug-ins/print to /usr/lib/gimp/2.0/print.orig by gimp-print
joergenlie@ubuntu:~$

I don't understand this, but it seems it doesn't say much about firefox

It seems like the .ubuntu.mozilla(or something) folder is gone too?

Jørgen

---

### Post by nanotube on 2006-06-01
yes, that doesn't say anything about firefox, no active diversions for it.
hmm... ok, post output of
```
ls -al /usr/bin/fire* /usr/bin/mozilla*
```
let's see what you have in there.
also, let's see output 
```
sudo dpkg -L firefox |grep "/usr/bin"
```
(that will show all files that are installed by the firefox package in /usr/bin)
you said you tried reinstalling with apt-get, and it says it is installed? just in case, also post output of
```
sudo apt-get install firefox
```

---

### Post by joergenlie on 2006-06-02
joergenlie@ubuntu:~$ ls -al /usr/bin/fire* /usr/bin/mozilla*
ls: /usr/bin/fire*: Ingen slik fil eller filkatalog
lrwxrwxrwx 1 root root   25 2006-02-17 15:34 /usr/bin/mozilla -> /etc/alternatives/mozilla
-rwxr-xr-x 1 root root 5193 2006-05-22 03:13 /usr/bin/mozilla-thunderbird
joergenlie@ubuntu:~$

This says no such file or directory


joergenlie@ubuntu:~$ sudo dpkg -L firefox |grep "/usr/bin"
Password:
/usr/bin
/usr/bin/firefox
/usr/bin/mozilla-firefox
joergenlie@ubuntu:~$

sudo apt-get firefox: already newest version.


Strange problem. I do appreciate your help, though:p 

Thank you!

Jørgen

---

### Post by joergenlie on 2006-06-02
Solved!

I managed to get dapper firefox to work after i removed it thru apt and reinstalled it thru aptitude:p 

Jørgen

---

### Post by nanotube on 2006-06-03
[QUOTE=joergenlie]Solved!

I managed to get dapper firefox to work after i removed it thru apt and reinstalled it thru aptitude:p 

Jørgen[/QUOTE]
ah cool. aptitude saves the day yet again. :)

---

### Post by FastZ on 2006-06-04
Hey guys, first of all, thanks for making that script to automate the install of the newest version of Firefox.  That's a Godsend.  

Secondly, I ran into a few problems, some I've managed to fix on my own, some I've not been able to figure out.  This is from a clean install of Ubuntu Breezy which has Firefox v1.0.8 (at the moment) that I would like to upgrade to v1.5.0.4.  Now, after downloading and CHMODing the script and running the ./installnewfirefox.sh command, it downloads the newest version, looks like it's installing it (going too fast for me to read), and then stops and errors out with the following error:

```
Removing the unzipped .tar.gz


Linking plugins


Linking launcher to new Firefox

dpkg-divert: Cannot divert directories

You need --help.
Previous command did not complete successfully. Exiting.

```

Now, I dont know what I need to do to fix that.  The problem I had right before this one was the libtotem plugins needed to be removed.  I did that and carried on and wound up here with this error.  Any and all help would be greatly appreciated.  I'm sort of a newb but I know enough to get by with the simple stuff so you may need to dumb it down a bit when trying to explain things to me.  :cool:

---

### Post by nanotube on 2006-06-05
[QUOTE=FastZ]Hey guys, first of all, thanks for making that script to automate the install of the newest version of Firefox.  That's a Godsend.  

Secondly, I ran into a few problems, some I've managed to fix on my own, some I've not been able to figure out.  This is from a clean install of Ubuntu Breezy which has Firefox v1.0.8 (at the moment) that I would like to upgrade to v1.5.0.4.  Now, after downloading and CHMODing the script and running the ./installnewfirefox.sh command, it downloads the newest version, looks like it's installing it (going too fast for me to read), and then stops and errors out with the following error:

```
Removing the unzipped .tar.gz


Linking plugins


Linking launcher to new Firefox

dpkg-divert: Cannot divert directories

You need --help.
Previous command did not complete successfully. Exiting.

```

Now, I dont know what I need to do to fix that.  The problem I had right before this one was the libtotem plugins needed to be removed.  I did that and carried on and wound up here with this error.  Any and all help would be greatly appreciated.  I'm sort of a newb but I know enough to get by with the simple stuff so you may need to dumb it down a bit when trying to explain things to me.  :cool:[/QUOTE]
that's strange... but at any rate,t he divert stuff comes at the end of installation, when everything is just about done. so we can fix it up.

can you post the output of command 
```
dpkg-divert --list
```

also post output of command 
```
ls -al /usr/bin/*fire*
```

---

### Post by FastZ on 2006-06-05
I wish I had checked back here sooner.  I upgraded to Ubuntu 6.0.6 last night before bed.  I might go back to Breezy this evening after work just so I can get you those outputs.  I'll let you know.  Haven't used your script to update Firefox 1.5.0.3 in Dapper yet.  Will try that before going back to Breezy just to see if it works.  Like I said, I'll let you know what the output of those commands are later this evening.

---

### Post by nanotube on 2006-06-05
[QUOTE=FastZ]I wish I had checked back here sooner.  I upgraded to Ubuntu 6.0.6 last night before bed.  I might go back to Breezy this evening after work just so I can get you those outputs.  I'll let you know.  Haven't used your script to update Firefox 1.5.0.3 in Dapper yet.  Will try that before going back to Breezy just to see if it works.  Like I said, I'll let you know what the output of those commands are later this evening.[/QUOTE]
ok, i'll be around. ;)

---

### Post by aysiu on 2006-11-05
In case anyone's interested, *nanotube*'s added some additions to the script:

It now works in Breezy, Dapper, and Edgy.

If you're having trouble with key verifications for the download, the script now allows you to continue without the verification, should you wish to do so.

It also symlinks the entire Firefox plugins directory to /opt/firefox/plugins instead of symlinking the individual plugins themselves. This way, if you add more plugins through *aptitude* or Synaptic or Adept, the plugins will be available with your newly installed Mozilla build Firefox.

---

### Post by nanotube on 2006-11-05
Thanks for updating this thread, aysiu. :)

to give credit where it's due, I will also note that aysiu made a number of very useful suggestions and comments (he was basically the driver for all the new additions to this iteration of the script - i was just the implementor), and also did all the testing to make sure it works. 

the script lives on both my site ([http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles)) as well as aysiu's site ([http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox))

I will also add a strong encouragement for everyone who uses this script and runs into problems to let me know. Any feature suggestions or possible improvements are also very welcome.

---

### Post by jis on 2006-11-07
> **aysiu said:**
> 
The script install Firefox 2.0 to the /opt directory and symlinks it so that the command *firefox* launches Firefox 2.0 (Mozilla build) and the command *firefox.ubuntu* launches Firefox 1.5 (Ubuntu build).


Thanks.

I have some remarks about the installnewfirefox.sh vs. install-swiftfox.sh:

installnewfirefox.sh
[LIST]
[*]has a localization chooser that gives some extra invalid options that could be removed with help of the Mozilla Foundation. (The script makes some assumptions of Mozilla's site.)
[*]downloads the binaries from mozilla.org, the well known Mozilla's site.
[*]gives option to assure the integrity of the download, although I think it does not protect against man-in-the-middle attack and does not reveal if Mozilla's download site has been compromized.
[/LIST]

whereas
install-swiftfox.sh
[LIST]
[*]downloads the binaries from getswiftfox.com, which claims to serve optimized binaries and to be Jason Halme's site, but who knows him?
[/LIST]

---

### Post by aysiu on 2006-11-07
This is something *nanotube* and I differ on actually.

I'm not sure of how well the key verification guards you against a Mozilla server compromise, but I suppose it's better than nothing, and it can be avoided if you want to avoid it.

I don't know about the Swiftfox builds or who created them.

Maybe *nanotube* can it explain it a little better.

---

### Post by jis on 2006-11-07
If the file is signed by some private key, and if you have the respective public key, it is very hard to fool you (i.e. downloader). It would be easier, if there was only some (hash) checksum that depends only on the file. But how do you get the public key?

---

### Post by nanotube on 2006-11-08
> **jis said:**
> If the file is signed by some private key, and if you have the respective public key, it is very hard to fool you (i.e. downloader). It would be easier, if there was only some (hash) checksum that depends only on the file. But how do you get the public key?

the public key is on file with a lot of keyservers. the install script picks up the mozilla key off one of them (subkeys.pgp.net). So, even if the mozilla ftp site was compromised and a trojaned tar.gz was uploaded, they would not be able to fake the pgp signature, which requires the use of the mozilla private key (presumably a very well-protected piece of info). 

so, this would generally be good protection also against MITM attacks, since not only would our MITM have to be between you and mozilla.org, but also between you and subkeys.pgp.net, to be able to send you both a compromised binary, as well as a fake key. so, it would have to be a very sophisticated attack, targeting you specifically, and having the foreknowledge that you are "about to" install the official mozilla build of firefox, and to verify the gpg key, using that particular pgp server. not something i'd be losing sleep over, honestly. :)

as to swiftfox - it's just a guy who makes optimized builds of the firefox code. certainly his "trustworthiness" is less than that of the mozilla organization, since he's just "a dude". But he's been at it for a while, and his work can be easily confirmed for the absence of any code modifications by making a build of the firefox code with the exact same compiler flags that he uses (he publishes those with every optimized build). If there are no illicit code mods, your binary build should be byte-for-byte the same as his binary build. So... presumably if he were making some code mods and not telling anyone, "someone" would have noticed by now. at least that's the usual opensource logic. :)

and by the way, jis, feel free to take the discussions we have about the script over email onto this thread. this will allow other interested parties to comment.

---

### Post by jis on 2006-11-08
Could the Firefox users that installed via the script subscribe to notifications that would tell when there are updates available? Maybe ubuntuforums.org could be used? Who would maintain the thread?

---

### Post by jis on 2006-11-08
Could you add remarks to your instructions for the script that it can use a copy of preloaded tarball in user's home directory, but deletes the copy after it has been extracted?

---

### Post by aysiu on 2006-11-08
*nanotube*, in answer to your PM, I think *jis*'s proposed phrasing would be great. I'm definitely in favor of calling it an "installation file" instead of a ".tar.gz."

---

### Post by fakie_flip on 2006-11-08
> **aysiu said:**
> **Introduction**
Starting with the second post in this thread, *nanotube* brought to life a sophisticated script translating the many copy-and-paste commands from the Ubuntu Wiki for getting the Mozilla (not Ubuntu) build of Firefox installed.
...

If I install FF2 by the script, how can I undo/uninstall everything that the script did? Is there another script? Some instructions on how to do it manually would be good. Thanks.

Second question:
Will this cause problems with the package manager sense no package manager will recognize the FF2 that is there from the script? Couldn't one of the package managers try to overwrite something from the script not seeing that it is there and/or cause other problems?

---

### Post by aysiu on 2006-11-08
> **fakie_flip said:**
> If I install FF2 by the script, how can I undo/uninstall everything that the script did? Is there another script? Some instructions on how to do it manually would be good. Thanks. As a matter of fact, I created an uninstall script, available on this page: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

There are also manual instructions available here, too:
[http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion)

> Second question:
Will this cause problems with the package manager sense no package manager will recognize the FF2 that is there from the script? Couldn't one of the package managers try to overwrite something from the script not seeing that it is there and/or cause other problems? No, no problems. It's completely separate. The package manager never touches the /opt directory.

---

### Post by fakie_flip on 2006-11-08
f

---

### Post by fakie_flip on 2006-11-08
I saw from some instructions that showed the script being run not as root, and then I looked at the script and saw a bunch of sudos. I'd like to have it keep going while I am asleep because the computer I will be using it on has dial up and the downloading is quite large for dial up, but I don't know if the script is going to stop while I am asleep waiting for some user input. Besides asking me for those user inputs, the script could keep asking me for the sudo password waiting for that before going on to the next. Is it a problem to just run the script like this instead?

sudo ./installnewfirefox.sh

I was asking if the script would conflict with the package manager because I didn't know what would happen when the package manager tried to upgrade the ubuntu's installed version of firefox and what it would think of the firefox.ubuntu link instead and if that install had been moved around or if it would confuse the new firefox with the old one for being in the same place or following one of the symbolic links.

---

### Post by fakie_flip on 2006-11-09
I am waiting for Swiftfox2 deb to download on this slow dial up internet.

---

### Post by nanotube on 2006-11-09
> **jis said:**
> Could the Firefox users that installed via the script subscribe to notifications that would tell when there are updates available? Maybe ubuntuforums.org could be used? Who would maintain the thread?

well, i guess the simplest thing if one wants auto notifications of available updates is to just subscribe to an RSS feed on mozilla.org. eg, the mozillazine news always has all the new release announcements on it: [http://www.mozilla.org/news.rdf](http://www.mozilla.org/news.rdf)

another thing that we could do is, at the time of installation, offer the user the option to put in a cron job, that automatically checks for new version say, every day, and when a new one is available, puts in a tray icon with update notification (kinda like the official ubuntu updater), and tells them that they should update their firefox. this should be a pretty simple to code shell script (with the help of zenity). 

what do y'all think about it?

---

### Post by nanotube on 2006-11-09
> **aysiu said:**
> *nanotube*, in answer to your PM, I think *jis*'s proposed phrasing would be great. I'm definitely in favor of calling it an "installation file" instead of a ".tar.gz."

ok, will let you know when i have the new version up.

---

### Post by nanotube on 2006-11-09
> **jis said:**
> Could you add remarks to your instructions for the script that it can use a copy of preloaded tarball in user's home directory, but deletes the copy after it has been extracted?

hmm, i suppose we could put in a little paragraph on "if you are doing an install on multiple machines" on the webpage. but on the other hand, would this even be a common enough case to warrant writing the extra paragraph? :)

---

### Post by nanotube on 2006-11-09
> **fakie_flip said:**
> I saw from some instructions that showed the script being run not as root, and then I looked at the script and saw a bunch of sudos. I'd like to have it keep going while I am asleep because the computer I will be using it on has dial up and the downloading is quite large for dial up, but I don't know if the script is going to stop while I am asleep waiting for some user input. Besides asking me for those user inputs, the script could keep asking me for the sudo password waiting for that before going on to the next. Is it a problem to just run the script like this instead?

sudo ./installnewfirefox.sh

I was asking if the script would conflict with the package manager because I didn't know what would happen when the package manager tried to upgrade the ubuntu's installed version of firefox and what it would think of the firefox.ubuntu link instead and if that install had been moved around or if it would confuse the new firefox with the old one for being in the same place or following one of the symbolic links.

well, two answers to your question: first, no, it shouldn't be a problem to just run the whole thing as root, it will work just as well. 
but second - right after the script finishes downloading firefox, it will ask you if you want to verify the gpg key - so it requires user input right after finishing the download anyway, so running it as sudo won't help :)

i am wondering, would it make sense to have an option in the script to run in "unattended" mode? so you can set some config variables at the top (choice of version, localization, gpgverification), and then just set it to go. would especially be useful if you are installing on multiple machines. any thoughts on this?

---

### Post by fakie_flip on 2006-11-09
> **nanotube said:**
> well, two answers to your question: first, no, it shouldn't be a problem to just run the whole thing as root, it will work just as well. 
but second - right after the script finishes downloading firefox, it will ask you if you want to verify the gpg key - so it requires user input right after finishing the download anyway, so running it as sudo won't help :)

i am wondering, would it make sense to have an option in the script to run in "unattended" mode? so you can set some config variables at the top (choice of version, localization, gpgverification), and then just set it to go. would especially be useful if you are installing on multiple machines. any thoughts on this?

Okay, I wasn't sure about all that last night. The computer is my girlfriend's running Dapper Drake at her house with dial up. I made her a small simple script. It downloaded a deb of Swiftfox 2 for her processor type. Then after the downloading was complete, it used poff to turn off the internet connection. Then to make sure the internet connection was turned off, it rebooted her computer. This morning she emailed me and said all went good. Tonight I am going to the San Antonio Linux User Group meeting to learn about Kickstart and talk with some cool people there.

Some people do not like automated installs without the user clicking "Okay" because they are afraid something can go wrong. It's fine with me. I've had to fix plenty of things with Linux. For me, my automated script has never caused a problem. After reading what was on your website, I will start using aptitude instead of apt-get. I've been looking for a way to remove those not needed dependencies from my system, and I never knew aptitude had that built in feature. I have a script I made. Cron runs it each early morning at 3:30 am.

```

#!/bin/bash
if [ `/usr/bin/whoami` != "root" ]; then
/bin/echo "You must be root to execute this script."
exit 67 # non-root exit error
fi
/usr/bin/apt-get update
/usr/bin/apt-get upgrade -y
/bin/echo "----------------------------------------------" >> /tmp/mylog
/bin/echo "Apt successfully updated the system:" >> /tmp/mylog
/bin/echo $(/bin/date) >> /tmp/mylog
/bin/echo >> /tmp/mylog
/bin/ls -luh /var/cache/apt/archives/ >> /tmp/mylog
/bin/echo >> /tmp/mylog
/bin/cat /tmp/mylog | /usr/bin/tee -a /var/log/pkgsbyapt | /usr/bin/sendEmail -t mine@gmail.com -f root@chris1.myftp.org -u "Re: Apt successful system update" -q
/bin/rm -f /tmp/mylog
/usr/bin/apt-get clean
exit 0 # completed successfully

```

---

### Post by nanotube on 2006-11-09
> **fakie_flip said:**
> Okay, I wasn't sure about all that last night. The computer is my girlfriend's running Dapper Drake at her house with dial up. I made her a small simple script. It downloaded a deb of Swiftfox 2 for her processor type. Then after the downloading was complete, it used poff to turn off the internet connection. Then to make sure the internet connection was turned off, it rebooted her computer. This morning she emailed me and said all went good. Tonight I am going to the San Antonio Linux User Group meeting to learn about Kickstart and talk with some cool people there.


why do you need to have the net connection off in order to install swiftfox? i'd think it would work just as well if you didn't disconnect while installing...

have fun at the LUG meeting :)

---

### Post by nanotube on 2006-11-10
Made a new version of the installation script. changes: 
change message for removing installation files to be more friendly
use ftp protocol to get the localizations list - this gives us a consistent dir list structure, and lets us avoid spurious localizations.

please test :)
```

#!/bin/bash
#
# installnewfirefox.sh
#               Script to automatically download and install the newest firefox version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
# 
# Author:       nanotube <nanotube@users.sf.net>.
#               
# Version:      installnewfirefox.sh  2.13  09-Nov-2006  nanotube@users.sf.net
# 
#
#######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

## Set version-specific variables
if grep -q "5.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/mozilla-firefox/plugins
elif grep -q "6.06" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
elif grep -q "6.10" /etc/issue ; then
  PLUGINPATH=/usr/lib/firefox/plugins
else
  echo "This script only works on Breezy, Dapper, or Edgy."
  exit 1
fi

## Get the newest firefox release version from mozilla website
VERSION=`wget -q -O - http://www.mozilla.com |grep "product=" -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'`

echo -e -n "The most recent release of firefox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
  read ans
  case $ans in
        Y|y|[Yy][Ee][Ss]) 
            break ;;
        N|n|[Nn][Oo]) 
            echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; 
            exit ;;
        *) 
            echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Get available localizations
LOCALIZATIONS=( ` wget -q -O - ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.8/linux-i686/ | grep "Directory" |grep -v "xpi" |awk '{print $7}' | awk -F\/ '{print $10}'` )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for firefox. Enter the number of your choice from the list below."
for ((i=0; i < LIMIT ; i++))
do
  echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
  read CHOICE
  if echo -n "$CHOICE" | grep -q "[^0-9]"; then
    echo -n "Your input contains non-numeric characters. Please try again: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ -z "$CHOICE" ]; then
    echo -n "Please enter the number of your choice from the list: "
    CHOICE=$(($LIMIT + 1))
    continue
  elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
    echo -n "Your input is not in the range of available localizations. Please try again: "
  fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
  read ans
  case $ans in
        Y|y|[Yy][Ee][Ss]) break ;;
        N|n|[Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
         *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

## Proceed to download and install firefox.

echo -e "\nUpdating repositories list\n"
sudo aptitude update

echo -e "\nMaking sure libstdc++5 and the old Firefox are installed\n"
sudo aptitude install firefox libstdc++5

if [ -d ~/.mozilla ]; then
  echo -e "\nBacking up old Firefox preferences\n"
  cp -R ~/.mozilla ~/.mozilla_backup_`date -Iseconds`
else
  echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd

echo -e "\nDownloading Firefox from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz

echo -e -n "The next step will verify the GPG signature for the firefox archive to assure its integrity. This step is important for your security. However, if you have problems getting this to work right, you may choose 'no' and proceed to installation without signature verification. Do you want to verify the signature [y/n]?"
while true
do
  read ans
  case $ans in
        Y|y|[Yy][Ee][Ss]) 
            echo -e "\nDownloading Firefox signature from the Mozilla site\n"
            wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz.asc

            echo -e "\nImporting Mozilla Software Releases public key\n"
            echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
            gpg --keyserver subkeys.pgp.net --recv 1AF32821

            echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
            gpg --verify firefox-$VERSION.tar.gz.asc firefox-$VERSION.tar.gz
            break ;;
        N|n|[Nn][Oo]) 
            echo "Proceeding without signature verification..."; break ;;
         *) 
            echo -n "Invalid command. Please answer yes or no [y/n] " ;;
  esac
done

echo -e "\nUnzipping the .tar.gz file\n"
sudo tar -C /opt -xzf firefox-$VERSION.tar.gz

echo -e "\nRemoving installation file(s) to free up disk space\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc

echo -e "\nLinking plugins\n"
sudo mv /opt/firefox/plugins /opt/firefox/plugins_`date -Iseconds`
sudo ln -s -f $PLUGINPATH /opt/firefox/plugins

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s -f /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s -f /opt/firefox/firefox /usr/bin/mozilla-firefox

echo -e "\nThe new Firefox version $VERSION has been installed successfully."

exit
```

---

### Post by fakie_flip on 2006-11-10
> **nanotube said:**
> why do you need to have the net connection off in order to install swiftfox? i'd think it would work just as well if you didn't disconnect while installing...

have fun at the LUG meeting :)

The script is for running while she is away from her computer. When the download is complete, the internet connection is not needed anymore. She's not at the computer to turn it off. Dial up is not like dsl or cable where it stays on all the time, but some people do turn theirs off when they are not using it, so they are less likely to have their computers hacked. She needs her internet connection turned off, so people can call her house phone, and she might have a limit on the amount of hours per day to use the dial up. The plan was not to install Swiftfox as soon as it finished downloading. The plan was to have the Swiftfox downloading after she went to sleep, and then shut down the internet automatically when Swiftfox was finished downloading. She installed it the next day. The deb that said Swiftfox_2-1-something.deb was the same thing as Firefox 1.5.0.7, what she already had. We thought Swiftfox2 was going to be the same as Firefox 2. Now we will be uninstalling it. Is there a way to make your script automatic, so she could keep it running while she is away, and it would not stop to wait for user input. One way would be to get all the user input immediately at the beginning, so it wouldn't need to ask for it later. The person could get it started, answer all of the questions, then leave. When the person comes back, it would be finished. If she runs the script that you have now while she is using the computer, it will download. That slows down everything else on dial up for her too much and often kicks her out of her gmail when she has done it before.

---

### Post by aysiu on 2006-11-10
> **nanotube said:**
> Made a new version of the installation script. changes: 
change message for removing installation files to be more friendly
use ftp protocol to get the localizations list - this gives us a consistent dir list structure, and lets us avoid spurious localizations.

please test :) Tested it. It works flawlessly.

One nitpick, though. If we're going to change the output to say > Removing installation file(s) to free up disk space doesn't it then seem weird to have right before that... ```
Unzipping the .tar.gz file
``` ...?

Maybe we should say, "Preparing installation files" or "Unpacking installation files"? Too much hiding?

---

### Post by jis on 2006-11-10
> **nanotube said:**
> well, i guess the simplest thing if one wants auto notifications of available updates is to just subscribe to an RSS feed on mozilla.org. eg, the mozillazine news always has all the new release announcements on it: [http://www.mozilla.org/news.rdf](http://www.mozilla.org/news.rdf)

another thing that we could do is, at the time of installation, offer the user the option to put in a cron job, that automatically checks for new version say, every day, and when a new one is available, puts in a tray icon with update notification (kinda like the official ubuntu updater), and tells them that they should update their firefox. this should be a pretty simple to code shell script (with the help of zenity). 

what do y'all think about it?

Great ideas. Maybe RSS feeds would be new thing for some users so they might need some additional guidance. I wonder if the latter idea would work with various desktop environments and window managers?

---

### Post by jis on 2006-11-10
> **nanotube said:**
> 
i am wondering, would it make sense to have an option in the script to run in "unattended" mode? so you can set some config variables at the top (choice of version, localization, gpgverification), and then just set it to go. would especially be useful if you are installing on multiple machines. any thoughts on this?

I think it is good idea to ask the options in the beginning. But if you are installing on several machines, you propably don't want to select the localization, version, and verification over and over again. Could the script be modified so that the queries and downloading would be skipped, if the script had a command line argument that is the path of the pre-loaded tarball? On the other hand the script could be used for selecting, downloading and verifying the desired tarball, as well.

---

### Post by fakie_flip on 2006-11-10
Maybe I will just upgrade to Edgy and have FF2 by doing this.
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by jis on 2006-11-10
> **nanotube said:**
> Made a new version of the installation script. changes: 
change message for removing installation files to be more friendly
use ftp protocol to get the localizations list - this gives us a consistent dir list structure, and lets us avoid spurious localizations.


Great, but why do you use FF version 1.5.0.8 as reference for localizations? 

What happens if the tarball's signature is bad? Does the script still install Firefox?

I installed FF 2.0 using installnewfirefox.sh on Xubuntu first time. Few notes:

I had FF 1.5 running during the script was running. I could run the upgraded FF only after I had quited the FF 1.5. (FF 2.0 asked whether to set itself as default browser, when I finally succeeded to launch FF 2.0. FF 2.0 could also update the extensions I have for FF.) Generally, I find it impossible to run both versions at the same time.

Some fonts are different in the new version, IMO they are worse.

---

### Post by nanotube on 2006-11-11
> **jis said:**
> Great, but why do you use FF version 1.5.0.8 as reference for localizations? 

Good catch! that's just because i copied some test code without correcting it. :) it should be generic. the new version has that bug fixed.

> 
What happens if the tarball's signature is bad? Does the script still install Firefox?

No, the script exits. Wouldn't want to install a corrupt archive, would we now? :)

> 
I installed FF 2.0 using installnewfirefox.sh on Xubuntu first time. Few notes:

I had FF 1.5 running during the script was running. I could run the upgraded FF only after I had quited the FF 1.5. (FF 2.0 asked whether to set itself as default browser, when I finally succeeded to launch FF 2.0. FF 2.0 could also update the extensions I have for FF.) Generally, I find it impossible to run both versions at the same time.

Some fonts are different in the new version, IMO they are worse.

well, both firefoxes try to use your .mozilla preferences directory, so yes, there may be trouble running the ubuntu firefox as well as the 2.0 archive. nothing we can do about that, since that's coded into firefox.

nothing we can do about the fonts either - whatever firefox comes with, that's what it is. :)

i still run 1.5.0.8 on mine (official mozilla build), and so maybe 2.0 did something different with the fonts? cuz stuff looks just fine for me...

---

### Post by nanotube on 2006-11-11
> **aysiu said:**
> Tested it. It works flawlessly.


excellent. but now thanks to jis pointing out the hard-coded firefox version (accidental), there's a new version out. :)

> 
One nitpick, though. If we're going to change the output to say  doesn't it then seem weird to have right before that... ```
Unzipping the .tar.gz file
``` ...?

Maybe we should say, "Preparing installation files" or "Unpacking installation files"? Too much hiding?

eh, i guess it makes sense. i changed the phrasing to say "extracting the downloaded firefox archive". nice and informative, without being too scary. :)

anyway, the newest version is up on pykeylogger site.

---

### Post by nanotube on 2006-11-11
> **jis said:**
> Great ideas. Maybe RSS feeds would be new thing for some users so they might need some additional guidance. I wonder if the latter idea would work with various desktop environments and window managers?

as for rss - well, they'd have to be using some kind of rss feed reader (or firefox itself)...

the cronjob - i don't know, i think the "tray icon" interface is standardized across gnome/kde, don't know about xfce, and definitely not about anything else out there... but, a simple gtk message box, instead of a tray icon, would be very cross-platform. but would people be too annoyed at a message box popping up in the middle of whatever they are doing?

---

### Post by nanotube on 2006-11-11
> **jis said:**
> I think it is good idea to ask the options in the beginning. But if you are installing on several machines, you propably don't want to select the localization, version, and verification over and over again. Could the script be modified so that the queries and downloading would be skipped, if the script had a command line argument that is the path of the pre-loaded tarball? On the other hand the script could be used for selecting, downloading and verifying the desired tarball, as well.

yea, commandline options would be the nicest implementation, i think... i will put that on the list for the next big version of the script ;) or maybe also allow for the setting of some configuration variables at the top of the script.

---

### Post by nanotube on 2006-11-11
> **fakie_flip said:**
> The script is for running while she is away from her computer. When the download is complete, the internet connection is not needed anymore. She's not at the computer to turn it off. Dial up is not like dsl or cable where it stays on all the time, but some people do turn theirs off when they are not using it, so they are less likely to have their computers hacked. She needs her internet connection turned off, so people can call her house phone, and she might have a limit on the amount of hours per day to use the dial up. The plan was not to install Swiftfox as soon as it finished downloading. The plan was to have the Swiftfox downloading after she went to sleep, and then shut down the internet automatically when Swiftfox was finished downloading. She installed it the next day. The deb that said Swiftfox_2-1-something.deb was the same thing as Firefox 1.5.0.7, what she already had. We thought Swiftfox2 was going to be the same as Firefox 2. Now we will be uninstalling it. Is there a way to make your script automatic, so she could keep it running while she is away, and it would not stop to wait for user input. One way would be to get all the user input immediately at the beginning, so it wouldn't need to ask for it later. The person could get it started, answer all of the questions, then leave. When the person comes back, it would be finished. If she runs the script that you have now while she is using the computer, it will download. That slows down everything else on dial up for her too much and often kicks her out of her gmail when she has done it before.

well, that's for the next version of the script
in the meantime - you /can/ just download the tar.gz firefox archive first, overnight, whenever you want, and place it in the home directory (without renaming it). then run the script when you are ready. the script is smart enough to detect that the firefox archive is already present, and won't attempt to download it again.

i suppose that should be documented somewhere... ;)

---

### Post by jis on 2006-11-12
> **fakie_flip said:**
> Maybe I will just upgrade to Edgy and have FF2 by doing this.
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

This might be a good alternative, if you want to be a pioneer on latest software. I suggest you read forums threads and release notes about Edgy before upgrading.

---

### Post by jis on 2006-11-12
> **nanotube said:**
> yea, commandline options would be the nicest implementation, i think... i will put that on the list for the next big version of the script ;) or maybe also allow for the setting of some configuration variables at the top of the script.

Commandline options have the drawback that you need a user manual. What do you mean by configuration variables?

---

### Post by jis on 2006-11-12
> **nanotube said:**
> as for rss - well, they'd have to be using some kind of rss feed reader (or firefox itself)...

the cronjob - i don't know, i think the "tray icon" interface is standardized across gnome/kde, don't know about xfce, and definitely not about anything else out there... but, a simple gtk message box, instead of a tray icon, would be very cross-platform. but would people be too annoyed at a message box popping up in the middle of whatever they are doing?

As for rss - I guess I should start learning how to use them better :)

the cronjob - update-notifier works fine with Xfce - I can see the tray icon occasionally. But I don't know what is the case with other window managers, such as Ion3, that is available in Ubuntu's Universe repository ([http://en.wikipedia.org/wiki/Ion_%28window_manager%29)](http://en.wikipedia.org/wiki/Ion_%28window_manager%29)). I think it is best to make a way that works with every window manager, if it is not too much work. Additionally, there could be more sophisticated methods for different window managers.

---

### Post by nanotube on 2006-11-12
> **jis said:**
> Commandline options have the drawback that you need a user manual. What do you mean by configuration variables?

well, the more complex things get, the more need there is for documentation. that's just a fact of life. :) 

by config variables i mean, at the top of the script, there would be some variables that can be defined by editing the script, that would do the same thing as using commandline options. of course, they would also need documentation, but that documentation would be provided in the script itself, next to the variable definitions.

---

### Post by nanotube on 2006-11-12
> **jis said:**
> As for rss - I guess I should start learning how to use them better :)

well, one rss reader i have used was rssowl. it's pretty good. google also has an online rss reader you can set up. it's called the google reader. 

> 
the cronjob - update-notifier works fine with Xfce - I can see the tray icon occasionally. But I don't know what is the case with other window managers, such as Ion3, that is available in Ubuntu's Universe repository ([http://en.wikipedia.org/wiki/Ion_%28window_manager%29)](http://en.wikipedia.org/wiki/Ion_%28window_manager%29)). I think it is best to make a way that works with every window manager, if it is not too much work. Additionally, there could be more sophisticated methods for different window managers.
well, i think if i can make something that works with kde, gnome, and xfce, i will be happy enough. :) i mean, someone who is advanced enough to use a more obscure desktop environment will probably be conscientious enough to check for updates anyway. there are too many different WMs out there to cover them all.

but hey, we will get to that once i actually sit down and make something :)

---

### Post by jis on 2006-11-12
> **nanotube said:**
> well, the more complex things get, the more need there is for documentation. that's just a fact of life. :) 

by config variables i mean, at the top of the script, there would be some variables that can be defined by editing the script, that would do the same thing as using commandline options. of course, they would also need documentation, but that documentation would be provided in the script itself, next to the variable definitions.

I think the easiest usage for a typical end user would be that the script asks everything interactively in the beginning. Not much different from the current implementation. 

I think a commandline option is a good method, if a pre-loaded tarball is used, since then you can make it a part of bigger installation script and you don't have to modify the script for all cases. On the other hand, config variables would encourage users to check what the script really does :) And of course, user would have to be aware of such features to start with ;)

---

### Post by jis on 2006-11-22
> **nanotube said:**
> well, one rss reader i have used was rssowl. it's pretty good. google also has an online rss reader you can set up. it's called the google reader. 

well, i think if i can make something that works with kde, gnome, and xfce, i will be happy enough. :):)

I installed yarssr from the Universe repository. A quote from its description: "Yet Another RSS Reader is an RSS aggregator and reader that displays its results in the GNOME or KDE system tray (notification area)". In my experience it works with Xfce, too.

I suppose the RSS feed address for new Mozilla release announcements is [http://www.mozilla.org/news.rdf](http://www.mozilla.org/news.rdf)

---

### Post by fakie_flip on 2006-11-22
No scripts are needed to get Firefox 2. Doing it this way will have your package manager recognize that it is installed, and you will easily be able to remove it through your package manager. You can add the repo and get it through your package manager. Here is how to do it.

```

sudo su
cd /etc/apt/
cp sources.list sources.list_backup
echo 'deb http://getswiftfox.com/builds/debian unstable non-free' >> sources.list
aptitude update
apt-cache search swiftfox # now do you see the one for your cpu?
aptitude install swiftfox-athlon-xp # example only, install the one for your cpu

```

Now you will have a Firefox 2 with the Firefox 2 interface, but it is not called that. It is Swiftfox and it runs faster because it removes unnecessary parts of Firefox and has it optimized for your cpu. Do not be surprised what happens if you try to run both FF and SF at the same time. If you try that, you will get either two FF or two SF running instead, no damage done. SF will show up in your gnome menu, and you can remove it with your package manager or switch between it and FF.

---

### Post by jis on 2006-12-20
Are Sfiftfox's security updates there as early as Mozilla's?

Anyway, I think it is better to update the version installed by the script by changing its owner
```
sudo chown -R ${USER}:${USER} /opt/firefox
```
then start Firefox by
```
firefox -safe-mode
```
and after the update (where restart can be made as Firefox suggests?) by
```
sudo chown -R root:root /opt/firefox
```
Can you make this work as an update script?

---

### Post by matchstich on 2006-12-20
i got firefox 2.0 using the cats site . a few days ago.   how do i update it for the latest security updates put out by firefox?  when i check updates in preferences, it just grey's out.
thanks

---

### Post by aysiu on 2006-12-20
> **matchstich said:**
> i got firefox 2.0 using the cats site . a few days ago.   how do i update it for the latest security updates put out by firefox?  when i check updates in preferences, it just grey's out.
thanks
Close Firefox.

Press Alt-F2.

Type ```
gksudo firefox
``` Check for updates and install them. Close Firefox again.

Launch it the way you normally would.

---

### Post by jis on 2006-12-21
> **aysiu said:**
> 
Type ```
gksudo firefox
``` Check for updates and install them. Close Firefox again.

Launch it the way you normally would.

I suppose you can not launch it like that since the updates are installed only after the restart after you have checked for updates (in Help menu). Why don't try the way I give in the previous post, or the way Nanotube gives in [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Update_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Update_Official_Mozilla_Build_of_Firefox) (though I would add the -safe-mode option to prevent bad extensions to run as root priviledges)?

---

### Post by aysiu on 2006-12-21
> **jis said:**
> I suppose you can not launch it like that since the updates are installed only after the restart after you have checked for updates (in Help menu). Why don't try the way I give in the previous post, or the way Nanotube gives in [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Update_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Update_Official_Mozilla_Build_of_Firefox) (though I would add the -safe-mode option to prevent bad extensions to run as root priviledges)?
I just used that method to update my Firefox, and it worked just fine.

If you use *gksudo firefox*, there won't be any extensions (unless you installed extensions as root). This is **very** different from *sudo firefox*, which will use your user profile and launch Firefox as root.

---

### Post by jis on 2006-12-21
aysiu: You used what method? Did you choose "Restart Firefox Now" unlike Nanotube tells?

Ok, maybe safe-mode is not needed with gksudo. Can you give a reference?

---

### Post by aysiu on 2006-12-21
> **jis said:**
> aysiu: You used what method? Did you choose "Restart Firefox Now" unlike Nanotube tells?

Ok, maybe safe-mode is not needed with gksudo. Can you give a reference?
Yes, I chose **Restart Firefox Now**, closed it, and then launched Firefox as a normal user again, once the update took.

I don't need a reference for safe-mode being unnecessary. I saw that all my extensions and themes and bookmarks weren't there when I launched Firefox with ```
gksudo firefox
```

---

### Post by jis on 2007-02-25
aysiu, it seems that nanotube still disagrees with you about the "Restart Firefox Now" thing in the gksudo update method. Anyway here's a script I made to update firefox as normal user. I think this way is better in principle, because it does not allow Firefox to do anything as root. I just used it to update to 2.0.0.2.

P.S. There seems to be problem in the attached script. The parenthesis in an echo row confuse script interpretter. Just remove the parenthesis from the row 5.

---

### Post by jis on 2007-03-21
I have problem in updating to 2.0.0.3 by the fixed script of the previous message. Has somebody succeeded in updating to 2.0.0.3?

---

### Post by jis on 2007-03-21
The error message I get is attached. Permissions should be OK so I wonder why the update fails. (Downloading the update did long time and I had to run the update-firefox.sh script again after I removed the parenthesis.)

---

### Post by aysiu on 2007-03-21
If you're downloading updates (instead of doing a fresh install), you should launch Firefox with *sudo*: ```
gksudo firefox
```

---

### Post by jis on 2007-03-21
Actually I succeeded in downloading the updates, but not in installing them. Starting firefox by the command you gave did the trick. I didn't need gksudo when updating to 2.0.0.2 though. Thanks.

---

### Post by aysiu on 2007-04-01
Hey, nanotube, in case you're still keeping track of this thread, you may want to update the script once Feisty comes out. I think the current incarnation of the script validates for Breezy, Dapper, and Edgy.

If you don't have time to update it by Feisty's release date, I'll make the change myself and post it on Psychocats until you do make the revision. Hope things are going well for you.

---

### Post by nanotube on 2007-04-01
hey aysiu,

i will give it an update. is the pluginpath for feisty the same as for dapper and edgy?

things are well enough - semester's end is nigh. :) how about you?

---

### Post by aysiu on 2007-04-01
Yes, the plugin path is the same in Feisty as for Dapper and Edgy.

I'm doing pretty well. Good to hear from you.

---

### Post by nanotube on 2007-04-01
i updated the script for feisty (version 7.04, iirc?)
i haven't changed anything material besides the extra version pass-through, but feel free to give it a test run and let me know if you run into any problems. :)

---

### Post by aysiu on 2007-04-01
Yes, it's 7.04.

I'll give it a test-run and confirm afterwards that it works or doesn't work.

By the way, might it make sense for the script to simply test if you're using Warty, Hoary, or Breezy (in which case, it'll use /usr/lib/mozilla) and then assume that the path is otherwise /usr/lib/firefox? That way you wouldn't have to update it every six months?

---

### Post by nanotube on 2007-04-01
> **aysiu said:**
> Yes, it's 7.04.

I'll give it a test-run and confirm afterwards that it works or doesn't work.

By the way, might it make sense for the script to simply test if you're using Warty, Hoary, or Breezy (in which case, it'll use /usr/lib/mozilla) and then assume that the path is otherwise /usr/lib/firefox? That way you wouldn't have to update it every six months?

hey
i've thought about it as well... 
but we've never tested the script on warty of hoary, so i don't even know what the path was there, and, do we know what's going to be the plugin path for feisty+n ? 

but yes, generally i would like to have a "permanent" version of the script. :) is there a variable or something somewhere that stores the plugin path?
---
scrap all that. i just had an idea. do you happen to have a breezy (or earlier) box you can play with? if so, could you give me the output of
```
 sudo dpkg -L firefox |grep '/plugins$'
```
i think this will give us the plugins path correctly regardless of version, but since i only have a dapper at my disposal, can't test whether the earlier versions will be correct...

edit: a breezy livecd should work too, if you have one, doesn't have to be an installed system

---

### Post by aysiu on 2007-04-02
For Feisty, it's this: ```
/usr/share/firefox/chrome/en-US/locale/en-US/mozapps/plugins
/usr/share/firefox/chrome/toolkit/content/mozapps/plugins
/usr/share/firefox/chrome/classic/skin/classic/mozapps/plugins
/usr/lib/firefox/plugins
``` For Hoary, it's this: ```
Package 'firefox' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
``` But if I do ```
sudo dpkg -L mozilla-firefox |grep '/plugins$'
``` I get this in Hoary: ```
/usr/lib/mozilla-firefox/plugins
``` Hope that helps.

---

### Post by nanotube on 2007-04-02
yes, that does help. for one, it tells me that the script won't work on hoary as is, because it tries to make sure package "firefox" is installed (line 99), which seems like it would fail on hoary. 

anyway, for now, please test the following script snippet, that should properly detect the plugin path for any ubuntu version.

```
#!/bin/bash

if sudo dpkg -l firefox &> dev/null ; then 
    if [ `sudo dpkg -l firefox | grep 'firefox' |awk '{print $1}'` == 'ii' ]; then
        PLUGINPATH=`sudo dpkg -L firefox |grep 'firefox/plugins$'`
    else
        PLUGINPATH=`sudo dpkg -L mozilla-firefox |grep 'firefox/plugins$'`
    fi
elif sudo dpkg -l mozilla-firefox &> dev/null ; then 
    if [ `sudo dpkg -l mozilla-firefox | grep 'firefox' |awk '{print $1}'` == 'ii' ]; then
        PLUGINPATH=`sudo dpkg -L mozilla-firefox |grep 'firefox/plugins$'`
    else
        echo "Neither package 'firefox' nor package 'mozilla-firefox' is installed. Installation will be aborted, since this should not happen."
        exit 1
    fi
fi

echo $PLUGINPATH
```

it works on dapper, but it would be nice to get feisty's, hoary's, edgy's, and breezy's take on it. :)

btw, wow, you still have hoary sitting around? :)

---

### Post by aysiu on 2007-04-02
I don't have Hoary up right now, but, yes, I did have an old live CD lying around, so I'll try out the snippet later on that one.

For now, here's my Feisty output: ```
ubuntu@ubuntu:~$ chmod +x test.sh 
ubuntu@ubuntu:~$ ./test.sh 
./test.sh: line 3: dev/null: No such file or directory
./test.sh: line 9: dev/null: No such file or directory

ubuntu@ubuntu:~$ nano test.sh 
ubuntu@ubuntu:~$ ./test.sh 
Password:
/usr/lib/firefox/plugins
ubuntu@ubuntu:~$ 
``` The *nano test.sh* part is just changing ```
dev/null
``` to ```
/dev/null
```

---

### Post by aysiu on 2007-04-02
Okay. Booted up Hoary, and I get this weird output: ```
ubuntu@ubuntu:~$ ./test.sh
./test.sh: line 10: [: ==: unary operator expected
Neither package 'firefox' nor package 'mozilla-firefox' is installed. Installation will be aborted, since this should not happen.
``` That's odd, since when I try to install *mozilla-firefox*, it tells me it's already installed: ```
ubuntu@ubuntu:~$ sudo apt-get install mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
mozilla-firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by nanotube on 2007-04-02
> **aysiu said:**
> The *nano test.sh* part is just changing ```
dev/null
``` to ```
/dev/null
```

whoops, sorry, i don't know how that crept in there! :) and while i was there, fixed up a logic hole, too. so here's the new snippet:

```
#!/bin/bash

if sudo dpkg -l firefox &> /dev/null ; then 
    if [ `sudo dpkg -l firefox | grep 'firefox' |awk '{print $1}'` == 'ii' ]; then
        PLUGINPATH=`sudo dpkg -L firefox |grep 'firefox/plugins$'`
    else
        PLUGINPATH=`sudo dpkg -L mozilla-firefox |grep 'firefox/plugins$'`
    fi
elif sudo dpkg -l mozilla-firefox &> /dev/null ; then 
    if [ `sudo dpkg -l mozilla-firefox | grep 'firefox' |awk '{print $1}'` == 'ii' ]; then
        PLUGINPATH=`sudo dpkg -L mozilla-firefox |grep 'firefox/plugins$'`
    else
        echo "Neither package 'firefox' nor package 'mozilla-firefox' is installed. Installation will be aborted, since this should not happen."
        exit 1
    fi
else
    echo "Neither package 'firefox' nor package 'mozilla-firefox' exists in the repositories. Installation will be aborted, since this should not happen."
    exit 1
fi

echo $PLUGINPATH

exit 0

```

please post back as you test on the various versions. 
also, if you happen to be on breezy, check the

---

### Post by aysiu on 2007-04-02
I don't actually have a spare copy of Breezy, but I'll test Hoary probably tomorrow.

Here's the Feisty output: ```
ubuntu@ubuntu:~$ ./test.sh 
/usr/lib/firefox/plugins
```

---

### Post by nanotube on 2007-04-02
> **aysiu said:**
> Okay. Booted up Hoary, and I get this weird output: ```
ubuntu@ubuntu:~$ ./test.sh
./test.sh: line 10: [: ==: unary operator expected
Neither package 'firefox' nor package 'mozilla-firefox' is installed. Installation will be aborted, since this should not happen.
``` 

the unary operator bit is what makes the if statement fail. don't know why it's failing though... what's the version of bash on hoary? 

what's the output of
```
sudo dpkg -l mozilla-firefox | grep 'firefox' |awk '{print $1}'
```

what's the output of
```
if [ `sudo dpkg -l mozilla-firefox | grep 'firefox' |awk '{print $1}'` == 'ii' ]; then echo "bla"; fi

```

what's the output of 
```
if [ $(sudo dpkg -l mozilla-firefox | grep 'firefox' |awk '{print $1}') == 'ii' ]; then echo "bla"; fi

```

what's the output of
```
if [[ $(sudo dpkg -l mozilla-firefox | grep 'firefox' |awk '{print $1}') == 'ii' ]]; then echo "bla"; fi

```

---

### Post by nanotube on 2007-04-02
> **aysiu said:**
> I don't actually have a spare copy of Breezy, but I'll test Hoary probably tomorrow.

Here's the Feisty output: ```
ubuntu@ubuntu:~$ ./test.sh 
/usr/lib/firefox/plugins
```

heh well, at least feisty works. :)
i'm starting to suspect that it may make sense to just forget about hoary, and worry about feisty and  future versions...

---

### Post by aysiu on 2007-04-02
Yeah, I can't imagine too many people saying, "I'm running Hoary and want to upgrade to the newest Firefox." Such requests will likely be met with, "Why don't you just install a newer version? Hoary is two years old!"

Dapper, Edgy, and Feisty all have the plugins in /usr/lib/firefox/plugins, and I think that's how it's going to stay for at least Feisty+2.

Maybe you should just have the output of *cat /etc/issue* tell people the script works for only 6.06 or higher?

---

### Post by nanotube on 2007-04-02
well, i'll think about how to go about it... but at least getting rid of hoary makes the job easier. :)

i'm reluctant to stop breezy support though, especially since the script already works on breezy as is...

---

### Post by aysiu on 2007-04-02
> **nanotube said:**
> well, i'll think about how to go about it... but at least getting rid of hoary makes the job easier. :)

i'm reluctant to stop breezy support though, especially since the script already works on breezy as is...
Perhaps if the output of *cat /etc/issue* is 4.10 or 5.04, they get an error message saying the script doesn't support those versions. If it's 5.10, they get the 5.10 plugin path, and if it's 6.06 or above, they get the other plugin path?

Alternatively (although this makes more work for you, obviously), 4.10 and 5.04 could get a warning indicating the script has not been tested for those versions and asking if they want to proceed anyway with the 5.10 configuration, which could work?

At what point does Canonical stop supporting 5.04? 6.06 is considering a Long-Term Support release, and it's support cycle is three years. So won't 5.04 and 4.10 stop getting security updates soon?

---

### Post by nanotube on 2007-04-02
> **aysiu said:**
> Perhaps if the output of *cat /etc/issue* is 4.10 or 5.04, they get an error message saying the script doesn't support those versions. If it's 5.10, they get the 5.10 plugin path, and if it's 6.06 or above, they get the other plugin path?

Alternatively (although this makes more work for you, obviously), 4.10 and 5.04 could get a warning indicating the script has not been tested for those versions and asking if they want to proceed anyway with the 5.10 configuration, which could work?

that's what i was thinking. since versions prior to 5.10 are few, they can be enumerated specifically.

> 
At what point does Canonical stop supporting 5.04? 6.06 is considering a Long-Term Support release, and it's support cycle is three years. So won't 5.04 and 4.10 stop getting security updates soon?

according to [http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#List_of_releases](http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)#List_of_releases)
5.04 is already out of the support cycle, and 5.10 is going to be in another two weeks. if canonical is not supporting them, it probably doesn't make too much sense for us to spend much effort on them, either.

---

### Post by FuturePilot on 2007-04-02
Ah, worked perfectly on a fresh install of Dapper. Thanks aysiu:)

---

### Post by nanotube on 2007-04-02
ok, here's the new version of the whole thing. "should" work on any version of ubuntu. please test. :)

the changes are:
[LIST]
[*]add support for the older versions, of course
[*]let users of older versions opt out after a warning
[*]add debug commandline option that should help with testing if users run into problems
[*]set pluginpath automatically based on dpkg output (should take care of any changes in later versions, unless they change package name from "firefox" to something else (like iceweasel).)
[/LIST]

edit: i won't upload it to the main site until you give me an OK that it works.

```

#!/bin/bash
#
# installnewfirefox.sh
#               Script to automatically download and install the newest firefox version for linux, on an Ubuntu system.
#               Requires an internet connection to work (obviously).
#
# Author:       nanotube <nanotube@users.sf.net>
#
# Version:      installnewfirefox.sh  2.17  02-Apr-2007  nanotube@users.sf.net
#
# Where to get the freshest version: 
#               http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Firefox
#               http://pykeylogger.sourceforge.net/installnewfirefox.sh
#
#######

## Make sure that we exit if any commands do not complete successfully.
set -o errexit
trap 'echo "Previous command did not complete successfully. Exiting."' ERR

## Take care of some command line options
if [ "$1" == "-h" ]; then
    echo "Usage: $0 [-h] [-d]"
    echo "-h: print help"
    echo "-d: run with some debug output"
    exit 0
fi
if [ "$1" == "-d" ]; then
    DEBUG=true
else
    DEBUG=false
fi


## Set version-specific variables
if grep -q "4.10\|5.04" /etc/issue ; then
    PACKAGE="mozilla-firefox"
    #PLUGINPATH="/usr/lib/mozilla-firefox/plugins"
    echo "Warning: Ubuntu versions 4.10 and 5.10 have NOT been thoroughly tested with this script. Use at your own risk. Are you sure you want to proceed [y/n]? "
    while true
    do
        read ans
        case $ans in
            Y|y|[Yy][Ee][Ss]) 
                break ;;
            N|n|[Nn][Oo]) 
                echo "Thanks for trying, anyway. It is recommended that you upgrade to a newer version of Ubuntu."; 
                exit ;;
            *) 
                echo -n "Invalid command. Please answer yes or no [y/n] " ;;
        esac
    done
elif grep -q "5.10" /etc/issue ; then
    PACKAGE="firefox"
else
    PACKAGE="firefox"
    #PLUGINPATH="/usr/lib/firefox/plugins"
fi

## Some debug output
if $DEBUG ; then
    echo $PACKAGE
fi

## Get the newest firefox release version from mozilla website
VERSION=$(wget -q -O - http://www.mozilla.com |grep "product=" -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//')

echo -e -n "The most recent release of firefox is detected to be $VERSION. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.com/) Is it correct [y/n]? "
while true
do
    read ans
    case $ans in
        Y|y|[Yy][Ee][Ss]) 
            break ;;
        N|n|[Nn][Oo]) 
            echo "If this does not agree with the latest version as listed on mozilla.com, please contact nanotube@users.sf.net and let me know."; 
            exit ;;
        *) 
            echo -n "Invalid command. Please answer yes or no [y/n] " ;;
    esac
done

if $DEBUG ; then
    wget -q -O - ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/
fi

## Get available localizations
LOCALIZATIONS=( $(wget -q -O - ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/ | grep "ftp://ftp.mozilla.org" |grep -v "xpi" |awk '{print $7}' | awk -F\/ '{print $10}') )

LIMIT=${#LOCALIZATIONS[*]}

## Get user choice of localization

echo "Please choose the localization (language) for firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please contact nanotube@users.sf.net, and we will try to track down the problem.]"
for ((i=0; i < LIMIT ; i++))
do
    echo "$i: ${LOCALIZATIONS[$i]}"
done

CHOICE=$(($LIMIT + 1))

echo -n "Enter your choice of localization: "
while [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]
do
    read CHOICE
    if echo -n "$CHOICE" | grep -q "[^0-9]"; then
        echo -n "Your input contains non-numeric characters. Please try again: "
        CHOICE=$(($LIMIT + 1))
        continue
    elif [ -z "$CHOICE" ]; then
        echo -n "Please enter the number of your choice from the list: "
        CHOICE=$(($LIMIT + 1))
        continue
    elif [ "$CHOICE" -gt "$(($LIMIT-1))" -o "$CHOICE" -lt "0" ]; then
        echo -n "Your input is not in the range of available localizations. Please try again: "
    fi
done

echo -n "You have chosen localization \"${LOCALIZATIONS[$CHOICE]}\". Is that correct [y/n]? "
while true
do
    read ans
    case $ans in
        Y|y|[Yy][Ee][Ss]) break ;;
        N|n|[Nn][Oo]) echo "In that case, start over by running this script again."; exit ;;
        *) echo -n "Invalid command. Please answer yes or no [y/n] " ;;
    esac
done

## Proceed to download and install firefox.

echo -e "\nUpdating repositories list\n"
sudo aptitude update

echo -e "\nMaking sure libstdc++5 and the Ubuntu Firefox package are installed\n"
sudo aptitude install $PACKAGE libstdc++5

PLUGINPATH=$(sudo dpkg -L $PACKAGE |grep 'firefox/plugins$')

if $DEBUG ; then
    echo $PLUGINPATH
fi

if [ -d ~/.mozilla ]; then
    echo -e "\nBacking up old Firefox preferences\n"
    cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)
else
    echo -e "\nOld firefox preferences not found. Nothing to back up. Proceeding with installation.\n"
fi

echo -e "\nChanging to home directory\n"
cd

echo -e "\nDownloading Firefox archive from the Mozilla site\n"
wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz

echo -e -n "The next step will verify the GPG signature for the firefox archive to assure its integrity. This step is important for your security. However, if you have problems getting this to work right, you may choose 'no' and proceed to installation without signature verification. Do you want to verify the signature [y/n]?"
while true
do
    read ans
    case $ans in
        Y|y|[Yy][Ee][Ss]) 
            echo -e "\nDownloading Firefox signature from the Mozilla site\n"
            wget -c http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/$VERSION/linux-i686/${LOCALIZATIONS[$CHOICE]}/firefox-$VERSION.tar.gz.asc

            echo -e "\nImporting Mozilla Software Releases public key\n"
            echo -e "Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.\n"
            gpg --keyserver subkeys.pgp.net --recv 1AF32821

            echo -e "\nVerifying signature...\nNote: do not worry about \"untrusted key\" warnings. That is normal behavior for newly imported keys.\n"
            gpg --verify firefox-$VERSION.tar.gz.asc firefox-$VERSION.tar.gz
            break ;;
        N|n|[Nn][Oo]) 
            echo "Proceeding without signature verification..."; break ;;
         *) 
            echo -n "Invalid command. Please answer yes or no [y/n] " ;;
    esac
done

echo -e "\nExtracting the downloaded Firefox archive\n"
sudo tar -C /opt -xzf firefox-$VERSION.tar.gz

echo -e "\nRemoving installation file(s) to free up disk space\n"
rm -f firefox-$VERSION.tar.gz firefox-$VERSION.tar.gz.asc

echo -e "\nLinking plugins\n"
sudo mv /opt/firefox/plugins /opt/firefox/plugins_$(date -Iseconds)
sudo ln -s -f $PLUGINPATH /opt/firefox/plugins

echo -e "\nLinking launcher to new Firefox\n"
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s -f /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s -f /opt/firefox/firefox /usr/bin/mozilla-firefox

echo -e "\nThe new Firefox version $VERSION has been installed successfully."

exit

```

---

### Post by aysiu on 2007-04-02
Thanks, *nanotube*. I'm planning to test it on Hoary, Dapper, Edgy, and Feisty. I'll let you know the results.

---

### Post by aysiu on 2007-04-02
You're amazing!

It actually works in Hoary, and I even tested it with a Flash plugin to make sure it does.

In Hoary, *firefox* will launch the new Mozilla version and *firefox.ubuntu* will launch the old Ubuntu version. The plugin path is /usr/lib/mozilla-firefox/plugins and the script does the proper symlinking so that plugins in that directory work for both versions. Awesome.

I also tested it in Dapper and Edgy. Still works for those two.

Haven't tested it Feisty yet. I'm waiting to finish doing some updates there. Then I'll test it out there and post back the results here.

---

### Post by aysiu on 2007-04-02
Tested successfully in Feisty. I say "Let 'er rip."

I think you can safely keep this script as is indefinitely.

If you ever did (six months or a year or two years from now) want to tweak it further, here are some ideas--totally unnecessary, but I'm just throwing them out there.

1. Maybe ask about the GPG thing earlier so that those who are on slower connections or who just want to answer a few quick things and then walk away and let the script do the rest can do just that.

2. On a related note, if the GPG thing fails, the script exits completely. You then have to rerun everything to get back to the GPG thing to say "no." Maybe if it fails, the script could say something like "Verification failed for some reason, would you like to continue anyway?"

3. A lot of new users who want to install the latest version of Firefox from Mozilla actually have already downloaded the .tar.gz from the Mozilla website. Is there any easy way to have the script detect whether or not the .tar.gz is already in ~/ or ~/Desktop (the two most likely places) and the use that instead of redownloading the extra 9.2 MB of a new .tar.gz?

Once again, job well done, and I think you can just sit on this one for a while. If you're ever bored months or years from now, you can think about those three ideas. It's been a pleasure testing out your improvements to the script.

---

### Post by nanotube on 2007-04-05
> **aysiu said:**
> Tested successfully in Feisty. I say "Let 'er rip."

ok, it's been let rip :)

> I think you can safely keep this script as is indefinitely.
sounds great. thanks for your support in this department :)

> If you ever did (six months or a year or two years from now) want to tweak it further, here are some ideas--totally unnecessary, but I'm just throwing them out there.

1. Maybe ask about the GPG thing earlier so that those who are on slower connections or who just want to answer a few quick things and then walk away and let the script do the rest can do just that.

2. On a related note, if the GPG thing fails, the script exits completely. You then have to rerun everything to get back to the GPG thing to say "no." Maybe if it fails, the script could say something like "Verification failed for some reason, would you like to continue anyway?"

3. A lot of new users who want to install the latest version of Firefox from Mozilla actually have already downloaded the .tar.gz from the Mozilla website. Is there any easy way to have the script detect whether or not the .tar.gz is already in ~/ or ~/Desktop (the two most likely places) and the use that instead of redownloading the extra 9.2 MB of a new .tar.gz?

those are some good ideas. maybe after the semester is done, i will take a crack at these. the gpg sig failure handling in particular should definitely be improved as a first priority, i think.

> Once again, job well done, and I think you can just sit on this one for a while. If you're ever bored months or years from now, you can think about those three ideas. It's been a pleasure testing out your improvements to the script.

and on my part, it's been a pleasure working with you, just as in the past. i really appreciated your testing, your ideas, and your encouragement.

when/if i get to working on this again for some further improvements, you can count on me posting in this thread. :)

---

### Post by aysiu on 2007-04-05
Cool.

We'll be in touch.

---

### Post by aysiu on 2007-04-20
Nanotube, I haven't confirmed this yet (will within the next day), but a couple of support threads here seem to indicate Feisty might not have an /opt directory by default, in which case the scripts (this one and the Thunderbird one) may need to be modified to create the directory or use /usr/local/bin instead.

---

### Post by aysiu on 2007-04-20
[Turns out the /opt folder is missing only for those who did a fresh install of Feisty beta](http://ubuntuforums.org/showpost.php?p=2496086&postcount=20). Feisty final has the /opt folder.

For good measure, it couldn't hurt to do a "if folder /opt doesn't exist, create it" line in the scripts, but it shouldn't pose a big problem.

---

### Post by nanotube on 2007-04-22
hey aysiu,

updated both the firefox and thunderbird scripts.

changes for firefox script:
make sure /opt exists before installing

changes for thunderbird:
update the script to include a bunch of fancy logic that has been included in the firefox script over time (command line options, gpg key verification optional, maybe some other stuff)
take care of cases where the profile link ~/.thunderbird may already exist
take care of cases where link in /usr/bin/thunderbird may already exist

i think this covers all the notes you have sent me in the last couple of days? if i missed anything let me know!

before I post the scripts up on the site, please run a quick test or two to make sure they still work. :)
both scripts attached to this message.

---

### Post by Sak on 2007-04-22
Hey Nanotube,

I just gave the updated "installnewthunderbird.sh" script a go and it exits unexpectedly for me.  

Just after it finishes checking the repositories I get the following...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
./installnewthunderbird.sh: line 123: syntax error near unexpected token `;;'

```

---

### Post by aysiu on 2007-04-22
Yeah, thanks for doing that, Sak.

Message to anyone else: if you're not afraid of possibly using a non-working script (it won't break your system--it may just not install anything), please do test whatever Nanotube posts.

I test these scripts myself, but I can't account for every possible situation out there. I'm planning to test these two revised scripts tomorrow.

---

### Post by Billy McCann on 2007-04-22
installnewfirefox.sh worked on Feisty.  

```
The new Firefox version 2.0.0.3 has been installed successfully.
```

---

### Post by aysiu on 2007-04-22
> **Billy McCann said:**
> installnewfirefox.sh worked on Feisty.  

```
The new Firefox version 2.0.0.3 has been installed successfully.
```
And that's the one Nanotube attached a few posts back and not the one on pykeylogger or psychocats?

---

### Post by Sak on 2007-04-22
Hmm, that's weird.  I'm also running Feisty and tried the one that Nanotube posted a couple hours ago...

> **nanotube said:**
> 

changes for thunderbird:
update the script to include a bunch of fancy logic that has been included in the firefox script over time (command line options, gpg key verification optional, maybe some other stuff)
take care of cases where the profile link ~/.thunderbird may already exist
take care of cases where link in /usr/bin/thunderbird may already exist

i think this covers all the notes you have sent me in the last couple of days? if i missed anything let me know!

before I post the scripts up on the site, please run a quick test or two to make sure they still work. :)
both scripts attached to this message.

---

### Post by aysiu on 2007-04-22
Firefox still works.

I, too, got this error for Thunderbird: ```
./installnewthunderbird.sh: line 123: syntax error near unexpected token `;;'
``` It happens right after the repositories are updated and the script checks for *libstdc++5* and *mozilla-thunderbird*.

I haven't yet tested what happens when there's no /opt directory.

---

### Post by nanotube on 2007-04-22
thanks for testing the scripts, everyone. :)
so it looks like the firefox one works, but tb one does not.
here's a new version of the tb one,  should correct syntax error. please try running again.

---

### Post by aysiu on 2007-04-22
Take 'em live, nanotube.

I tried both with the /opt folder and both without the /opt folder.

I tried the new Thunderbird script with a ~/.mozilla-thunderbird profile and with ~/.thunderbird profile. And I had all the other symlinks in place before. No errors. No syntax error, either.

Thanks for the quick revision!

---

### Post by nanotube on 2007-04-22
> **aysiu said:**
> Take 'em live, nanotube.

I tried both with the /opt folder and both without the /opt folder.

I tried the new Thunderbird script with a ~/.mozilla-thunderbird profile and with ~/.thunderbird profile. And I had all the other symlinks in place before. No errors. No syntax error, either.

Thanks for the quick revision!

cool. they're live. :)
i hope i won't drown in bug reports now... ;)

---

### Post by nanotube on 2007-04-22
well, it appears that you guys haven't been testing the gpg key verification. i was just upgrading my own thunderbird to 2.0.0.0, and gpg key verification step failed to get the key. upon further investigation, turns out i was using an expired subkey. so i updated both the ff and the tb scripts to include a non-expiring key id, so now gpg verification works.

if you care to give it some further testing, the new versions are up on my site (since the only thing i did was update the key id, and since it worked for me in updating thunderbird, i just put them up there directly.

---

### Post by aysiu on 2007-04-22
That's odd. I didn't run into any problems with the gpg key verification.

I'll go ahead and test the new versions, though.

---

### Post by nanotube on 2007-04-22
> **aysiu said:**
> That's odd. I didn't run into any problems with the gpg key verification.

I'll go ahead and test the new versions, though.

hmm, strange. maybe they "just updated" the server listing or something...

please let me know if you run into any problems during testing.

---

### Post by mik9dt on 2007-04-22
Ijust tried your script to install thunderbird 2. 
It stoped after asking if I wanted to update my profile....
yes or no gives same result...
script stops

---

### Post by nanotube on 2007-04-22
> **mik9dt said:**
> Ijust tried your script to install thunderbird 2. 
It stoped after asking if I wanted to update my profile....
yes or no gives same result...
script stops

you mean after it asked to back up your profile? 
could you please post the output that you see up until the point that the script exits?

oh, and did you use the latest version of the script, which would be here:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Official_Mozilla_Build_of_Thunderbird)

the versions attached to the messages here are for testing purposes only.

---

### Post by mik9dt on 2007-04-22
ok so I downloaded again just to be sure.
I run it as instructed...... then I get this

"Do you want to make a backup of your old mozilla thunderbird profile (~/.mozilla-thunderbird)? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: y

Backing up old thunderbird preferences

You seem to have a thunderbird profile in ~/.thunderbird that is not a symbolic link to the default profile location at ~/.mozilla-thunderbird. To avoid any accidental profile mishaps, the script is going to terminate. Sort out your profiles, and then try again."

Well, I will do as instructed and report back later....

---

### Post by mik9dt on 2007-04-22
Ok I have installed thunderbird 2 :-)

I renamed ~/.thunderbird and ran script again.
Did not check gpg key as I had no succes the first time.

Success at last, thank you....

---

### Post by nanotube on 2007-04-23
mik9dt's experience (and another thread that shows that having a ~/.thunderbird directory may not be too rare of an occurrence) has prompted me to make the script a bit more robust in handling this case.

posting a new version. could you please test it in the situation when a directory ~/.thunderbird exists (not a link to .mozilla-thunderbird, but a directory, probably a copy of .mozilla-thunderbird). 

the script will now ask whether the user wants to 1. use this directory as the profile; 2. move it out of the way and use a link to .mozilla-thunderbird as the profile; or 3. exit now and figure things out later.

please test and report your results.

---

### Post by aysiu on 2007-04-23
> **nanotube said:**
> mik9dt's experience (and another thread that shows that having a ~/.thunderbird directory may not be too rare of an occurrence) has prompted me to make the script a bit more robust in handling this case.

posting a new version. could you please test it in the situation when a directory ~/.thunderbird exists (not a link to .mozilla-thunderbird, but a directory, probably a copy of .mozilla-thunderbird). 

the script will now ask whether the user wants to 1. use this directory as the profile; 2. move it out of the way and use a link to .mozilla-thunderbird as the profile; or 3. exit now and figure things out later.

please test and report your results.
I tried it with only a ~/.thunderbird profile (not a symlink), and I got this: ```
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

**Old thunderbird preferences not found. Nothing to back up. Proceeding with installation.**


Changing to home directory

``` Still worked, though (Thunderbird uses the existing profile).

---

### Post by nanotube on 2007-04-23
> **aysiu said:**
> I tried it with only a ~/.thunderbird profile (not a symlink), and I got this: ```
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

**Old thunderbird preferences not found. Nothing to back up. Proceeding with installation.**


Changing to home directory

``` Still worked, though (Thunderbird uses the existing profile).
hmm, well, that's as expected (although maybe it should back up ./~thunderbird as well?

but the "new" code is when you have both .tb and .moz-tb directories. but let me think about it and see how i want to restructure this...

---

### Post by nanotube on 2007-04-23
ok, new version to test. :)
please try the following combinations:
a profile in ~/.mozilla-thunderbird
a profile in ~/.thunderbird
a profile in both of those
a profile in neither of those
a profile in ~/.mozilla-thunderbird, and a link to it from ~/.thunderbird

the script should now be able to handle all of these possibilities.
new version of script is attached.

---

### Post by aysiu on 2007-04-23
I'll test those scenarios out and post any errors I get.

---

### Post by Billy McCann on 2007-04-24
> **aysiu said:**
> And that's the one Nanotube attached a few posts back and not the one on pykeylogger or psychocats?

yes.  sorry took so long.

---

### Post by nanotube on 2007-04-24
> **Billy McCann said:**
> yes.  sorry took so long.

no problem, thanks for testing. :)

---

