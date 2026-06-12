---
title: "Ubunto One Client Won't Start From Preferences"
date: 2010-03-30
forum: Ubuntu One (CLOSED)
---

### Post by jaco223 on 2010-03-30
I had ubuntu one working yesterday, by working I mean the client started up from preferences> ubuntu one. Today after doing some updates via update manager
it won't start. I would like to purge ubuntu one and start over. How do  I go about
doing this? Your help would be greatly appreciated.

Jaco

---

### Post by dabomb1022 on 2010-03-31
If your on 10.4 beta then this is a known issue

---

### Post by jaco223 on 2010-03-31
> **dabomb1022 said:**
> If your on 10.4 beta then this is a known issue

dabomb, it's strange sometimes the client works, and other times not. Thanks for the 
heads up.

Jaco

---

### Post by joshuahoover on 2010-03-31
> **jaco223 said:**
> dabomb, it's strange sometimes the client works, and other times not. Thanks for the 
heads up.

Jaco

This is likely due to ubuntuone-login hanging up. If you open a terminal session and run: killall ubuntuone-login

Then try to open Ubuntu One Preferences again to see if that works around the problem. 

Thank you,

Joshua

---

### Post by jaco223 on 2010-03-31
> **joshuahoover said:**
> This is likely due to ubuntuone-login hanging up. If you open a terminal session and run: killall ubuntuone-login

Then try to open Ubuntu One Preferences again to see if that works around the problem. 

Thank you,

Joshua

Joshua, thanks for the quick reply, at the moment ubuntu one is ok I have the client running now. It seems sometimes it will start up and sometimes not. It's weird if it doesn't start up from >preferences> ubuntu one, it will start from the me-menu. I did however purge ubuntu one early this morning. I checked my U1 account and everything uploaded and syncd. Thanks again, i'll continue to monitor the situation and report any odd behavior.

Thanks again,

Jaco

---

### Post by ubuntwinkel on 2010-04-13
Everyone seems to be able to get this to work eventually.  I'm still stuck.  

Briefly, selecting System > Preferences > UbuntuOne shortly results in an enormous error popup which displays the apparent contents of the UbuntuOne server response (screenshot attached).  Most of the error window extends well beyond the limits of the screen and is unreadable.  It contains all HTML code from a web server, intended to be rendered by a web browser, with information specific to the server, not the Ubuntu One client.  As best I can tell, the web page (if it were rendered properly) would tell me that authorization failed, without adding much detail, and would give me links to go elsewhere, none of which I can access. 

My UbuntuOne account is valid, web browser access to my account is fine, but no machines are associated yet as I cannot get past the above error in the UbuntuOne client.  

Because this was also failing (differently) with the Karmic repositories, I switched to using the newer ppa.launchpad.net repositories, and now the ubuntuone-client-gnome version is: 
1.1.3+r409-0ubuntu2~ppa1~karmic.

uname -a output is:
Linux blubox 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux

I suppose this may be a server issue, since what I assume to be the server response (in the popup) appears to be the contents of an OOPS-page.  But, at best, this is a buggy way to handle authorization errors.  

Hoping for suggestions... TIA.

---

### Post by joshuahoover on 2010-04-13
> **ubuntwinkel said:**
> Everyone seems to be able to get this to work eventually.  I'm still stuck.  

Briefly, selecting System > Preferences > UbuntuOne shortly results in an enormous error popup which displays the apparent contents of the UbuntuOne server response (screenshot attached).  Most of the error window extends well beyond the limits of the screen and is unreadable.  It contains all HTML code from a web server, intended to be rendered by a web browser, with information specific to the server, not the Ubuntu One client.  As best I can tell, the web page (if it were rendered properly) would tell me that authorization failed, without adding much detail, and would give me links to go elsewhere, none of which I can access. 

My UbuntuOne account is valid, web browser access to my account is fine, but no machines are associated yet as I cannot get past the above error in the UbuntuOne client.  

Because this was also failing (differently) with the Karmic repositories, I switched to using the newer ppa.launchpad.net repositories, and now the ubuntuone-client-gnome version is: 
1.1.3+r409-0ubuntu2~ppa1~karmic.

uname -a output is:
Linux blubox 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux

I suppose this may be a server issue, since what I assume to be the server response (in the popup) appears to be the contents of an OOPS-page.  But, at best, this is a buggy way to handle authorization errors.  

Hoping for suggestions... TIA.

My apologies for this error. It was a server side problem that is now fixed: [https://launchpad.net/+bug/562286](https://launchpad.net/+bug/562286)

Try the following from a terminal session:

killall ubuntuone-login 
ubuntuone-preferences

This should kill existing processes and start ubuntuone-preferences for you which will prompt you to add the computer to your Ubuntu One account.

Thank you,

Joshua

---

### Post by ubuntwinkel on 2010-04-13
That was easy (for me)!  Thanks Joshua!  And thanks to the Ubuntu One Desktop+ team!

---

### Post by ubuntwinkel on 2010-04-13
_[SIZE="5"]Update[/SIZE]_

I needed the ppa.launchpad.net version ([SIZE="1"]1.1.3+r409-0ubuntu2~ppa1~karmic[/SIZE]) to get my machine added to the Ubuntu One server, but then nothing would upload, and I had no panel icon.  I had to switch back to the Karmic version ([SIZE="1"]1.0.3-0ubuntu1[/SIZE]) and now all seems OK (fingers crossed).  

It's funny, though probably intentional, but the only Ubuntu One menu entry for the Karmic version is under 'Internet' (ubuntuone-client-applet), while the Ubuntu One menu entry using the newer ppa.launchpad.net version is only found under 'System > Preferences' (ubuntuone-preferences).  The scripts and binaries are all, not just updated, but reorganized and re-purposed from one version to the other as well.  I don't envy you guys trying to keep all this straight while bug-tracking.  I trust all this complexification is necessary somehow.  Keep up the good work.

---

### Post by tekstr1der on 2010-04-14
On latest lucid, ubuntuone has suddenly stopped working. The daemon is started successfully at system bootup, however upon running ubuntuone-preferences, the status shows a disconnected state. After selecting the "Connect" button, the status just hangs at "Synchronization in progress...".

The ubuntuone-login process appears to be hanging maybe? This is new behavior here. Ubuntu One has been working reliably throughout most of the lucid dev cycle. I can still log in successfully from the website, but I can no longer synchronize files.

EDIT: Even worse behavior now: I was curious to see if tomboy notes would still sync with the server. Tomboy sync works just fine still. However, upon syncing tomboy, the ubuntuone-preferences status shows "Synchronization complete" and nautilus displays the new/changed files with the green checkmark emblem. A quick check with the website reveals that this is falsely reporting success. No files have been synchronized. So, not only is Ubuntu One no longer working, it is also now misleading the user to believe that is is working properly. This has data-loss potential for sure!

---

### Post by joshuahoover on 2010-04-14
> **tekstr1der said:**
> On latest lucid, ubuntuone has suddenly stopped working. The daemon is started successfully at system bootup, however upon running ubuntuone-preferences, the status shows a disconnected state. After selecting the "Connect" button, the status just hangs at "Synchronization in progress...".

The ubuntuone-login process appears to be hanging maybe? This is new behavior here. Ubuntu One has been working reliably throughout most of the lucid dev cycle. I can still log in successfully from the website, but I can no longer synchronize files.

EDIT: Even worse behavior now: I was curious to see if tomboy notes would still sync with the server. Tomboy sync works just fine still. However, upon syncing tomboy, the ubuntuone-preferences status shows "Synchronization complete" and nautilus displays the new/changed files with the green checkmark emblem. A quick check with the website reveals that this is falsely reporting success. No files have been synchronized. So, not only is Ubuntu One no longer working, it is also now misleading the user to believe that is is working properly. This has data-loss potential for sure!

Sorry to hear files stopped synchronizing for you. If you can hop on #ubuntuone on Freenode IRC, we can probably help you in real time. I'm joshuahoover on there and am normally on from 13:00-21:00 UTC, Monday-Friday. If you can't get on there, please file a bug and be sure to include the debug files found in ~/.cache/ubuntuone/log. Without getting a look at these log files, it's tough to say what is going on and how we might fix it.

NOTE: Tomboy sync and files sync have no relation to one another. They have very different ways of synchronizing and authorizing, so one should not impact the other.

Thank you,

Joshua

---

### Post by terwilligerjones on 2010-04-30
I'm afraid I'm bitten, too. From the Me Menu, I click Ubuntu One. I get the preferences box. The preferences box correctly displays my name and email. The devices tab correctly identify the three computers on the account (all running 10.4). The preferences box indicates "Synchronization in progress". It reports 26.8 MB used and identifies that as 1.3% of my quota, but the nailbiter display never runs and "Synchronization in progress..." never goes away.

terwilliger

---

### Post by pricorp on 2010-05-01
I have the same issue.
After upgrading to Ubuntu 10.04, "Synchronization in progress..." appears in Ubuntu One Preferences for a while. Then "Disconnected" appears. No file has been synchronized.

---

### Post by lotharmat on 2010-05-01
The ubuntuone-preferences is what keeps hanging when I try and associate my laptop using Lucid.

---

### Post by mdshaver on 2010-05-01
same problem here

---

### Post by dulbirakan on 2010-05-03
Same here... It just hangs up and no files are synced. I will try to purge and reinstall to see if that will work.

---

### Post by dulbirakan on 2010-05-03
To anyone interested... purging-reinstalling did not work. I have removed all devices from U1 and ubuntuone-preferences still tries to connect eventhough no account is defined. Then after like 2 sec. it hangs up and becomes non-responsive. 

I realy wanted to use U1 but.. I guess it wont be soon.

---

### Post by pricorp on 2010-05-03
> **dulbirakan said:**
> To anyone interested... purging-reinstalling did not work. I have removed all devices from U1 and ubuntuone-preferences still tries to connect eventhough no account is defined. Then after like 2 sec. it hangs up and becomes non-responsive. 

I realy wanted to use U1 but.. I guess it wont be soon.

About 2 hours ago it started syncing on my x64 without any change from my side. 

It looks like it is an issue from the server side; see the bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/573800](https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/573800)

---

### Post by dulbirakan on 2010-05-03
I guess I messed something up while trying to fix things... I found some guide for complete removal in some other thread. Applying that seemed to improve things, if it syncs properly I might even remove dropbox...

[https://answers.launchpad.net/ubuntuone-client/+faq/778](https://answers.launchpad.net/ubuntuone-client/+faq/778)

---

### Post by joshuahoover on 2010-05-03
> **lotharmat said:**
> The ubuntuone-preferences is what keeps hanging when I try and associate my laptop using Lucid.

Our service has been experiencing large spikes in new users and overall use with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. Without seeing any logs, I can guess that you're being affected by these issues. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

While I don't know if you'll have much success syncing files with the service right now, you can try looking at the following FAQ for help: [https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?](https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?) Also, please be sure to run Upgrade Manager, as we released a bug fix that prevented some users from being able to open Ubuntu One Preferences.

My apologies for the inconvenience and thank you for your patience.

Joshua

---

