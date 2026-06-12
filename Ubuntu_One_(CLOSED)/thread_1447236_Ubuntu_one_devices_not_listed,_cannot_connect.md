---
title: "Ubuntu one devices not listed, cannot connect"
date: 2010-04-05
forum: Ubuntu One (CLOSED)
---

### Post by gkkg on 2010-04-05
I am on Lucid Beta 64bit.
I am having a problem connecting ubuntu one with my account. At the moment, in the 'devices' tab, the only machine listed is <local machine>. I try to click on 'connect', and get a 'synchronizing' then 'disconnected' message. 
This is happening after an initial setup that might have worked okay, but at first I found a long list of devices in the devices tab (all duplicates of one computer) and I decided to delete them all to start over. Now I am stuck with this <local machine> that will not connect. 
The strange thing is that I am able to sync Tomboy with U1, and I have two machines listed on my U1 account at the moment. But file sync will not work.
What can I do? I would be happy to simply delete all configuration files and start over, but I already tried deleting all the ubuntuone and couchdb hidden folders I could find with no effect, I also tried removing completely the client and reinstalling.

---

### Post by duanedesign on 2010-04-05
If  you see <local machine> it means you have deleted all your machines from your computer, but there is still a Token in the keyring. Please try the following.

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open System-> Preferences-> Ubuntu One (or Me Menu ->
       Ubuntu One)
   9. a web page should open, prompting you to add your computer to
       your Ubuntu One account
  10. Add your computer

Please let us know if this helps.

thank you,
duanedesign

---

### Post by NeverSage on 2010-05-01
I'm having the same problem and the solution didn't work.  It still says <LOCAL MACHINE> where my computer should be.  There is no Ubuntu One token to delete in Passwords and Encryption Keys.  I was able to delete my computer from the Ubuntu One site though.  I've uninstalled and reinstalled with no luck.  Any more suggestions?

Thanks

Edit: I'm running the 32bit Netbook Edition release

---

### Post by bacb on 2010-05-02
I'm in the same case with Ubuntu 10.04 32 bits. There is no Ubuntu One token to delete in Passwords and Encryption Keys.

---

### Post by joshuahoover on 2010-05-03
> **bacb said:**
> I'm in the same case with Ubuntu 10.04 32 bits. There is no Ubuntu One token to delete in Passwords and Encryption Keys.

Apologies to all those experiencing issues with setting up or using Ubuntu One right now. Our service has been experiencing large spikes in new users and overall use with the release of Lucid and is making certain key parts of the system to not function properly. We're working on fixing these problems. Without seeing any logs, I can guess that you're being affected by these issues. We'll keep you updated in two ways on our progress:

1) [http://identi.ca/ubuntuone](http://identi.ca/ubuntuone)
2) [https://wiki.ubuntu.com/UbuntuOne/Status](https://wiki.ubuntu.com/UbuntuOne/Status)

Again, apologies for the inconvenience and thank you for your patience.

Thank you,

Joshua

---

### Post by mdebusk on 2010-06-02
> **bacb said:**
> I'm in the same case with Ubuntu 10.04 32 bits. There is no Ubuntu One token to delete in Passwords and Encryption Keys.

Same problem (no token) here. I can connect from Ubuntu Netbook Edition 10.04, but not from my desktop with Ubuntu 10.04. Also, there's no configuration file in ~/.config/ubuntuone/ .

---

### Post by mdebusk on 2010-06-02
> **duanedesign said:**
> If  you see <local machine> it means you have deleted all your machines from your computer, but there is still a Token in the keyring.

I just upgraded from Hardy. There's never before been an Ubuntu One client on my desktop. Yes, I still get <local machine> here.

---

### Post by duanedesign on 2010-06-02
If you dont have a Token, you definetly need one. If you have no Token and your computer is not listed at [http://one.ubuntu.com/account/machines](http://one.ubuntu.com/account/machines) opening Ubuntu One should prompt the browser to open and present you with the option to add you computer. [(See Step 1)]("https://one.ubuntu.com/support/installation/")

If you are on lucid and are not seeing the 'Add your computer" button you might be experiencing a bug that is affecting some people. [See here.]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?") The workaround is to close Ubuntu One and run the following command:

```
 u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

Which should put you at step 2 of [this process]("https://one.ubuntu.com/support/installation/").

---

### Post by mdebusk on 2010-06-03
> **duanedesign said:**
> If you dont have a Token, you definetly need one. If you have no Token and your computer is not listed at [http://one.ubuntu.com/account/machines](http://one.ubuntu.com/account/machines) opening Ubuntu One should prompt the browser to open and present you with the option to add you computer.

Agreed. It doesn't. (Open the browser, that is.)

> ```
 u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

Which should put you at step 2 of [this process]("https://one.ubuntu.com/support/installation/").

I just tried that. Nothing happens. Output of [FONT="Fixedsys"]ps aux | grep ubuntuone[/FONT] shows both ubuntuone-syncdaemon and ubuntuone-login are running.

---

### Post by mdebusk on 2010-06-07
> **mdebusk said:**
> I just tried that. Nothing happens. Output of [FONT="Fixedsys"]ps aux | grep ubuntuone[/FONT] shows both ubuntuone-syncdaemon and ubuntuone-login are running.

I installed the recent update and tried again. Still nothing. No browser opens when it should.

Any idea how, specifically, it attempts to open the browser? What command it sends to the shell?

---

### Post by rdingraham on 2010-06-08
Similar problem.  I have an Ubuntu One account, which I signed up for on an old laptop.  I have a new computer and can not add it to my account.  All the Devices Tab says (In Ubuntu One Preferences) is <LOCAL MACHINE>.
I can log on to my Ubuntu One account through a browser, but it shows NO Devices listed in my account.  The installation instructions don't work, because Step #8 (Confirm Computer Access) does not come up.  I can not add my computer either locally or through the website.

Typing u1sdtool -q; killall ubuntuone-login; u1sdtool -c in the terminal does nothing.  It simply returns the message: ubuntuone-syncdaemon stopped, but it does not open a browser window.

Bob I.

---

### Post by Diabolis on 2010-06-12
> **NeverSage said:**
> I'm having the same problem and the solution didn't work.  It still says <LOCAL MACHINE> where my computer should be.  There is no Ubuntu One token to delete in Passwords and Encryption Keys.  I was able to delete my computer from the Ubuntu One site though.  I've uninstalled and reinstalled with no luck.  Any more suggestions?


At first, the fix didn't work for me, in the same context. But I forgot to stop ubuntu one.

My steps:
Stop completely ubuntu one.
```
ps -e | grep ubuntuone
kill -9 ####
kill -9 ####
kill -9 ####

```
I logged out from the ubuntuone website.
Opened ubuntuone preferences window / manage account.
I logged in to ubuntuone website and it finally asked me to select my pc.
Closed ubuntuone preferences window.
Opened ubuntuone preferences window and now it showed under devices my pc.

---

### Post by Ceezey77 on 2010-10-18
I'm running Ubuntu 10.04 - had the very same issue and ran the fix below.  Worked first time! Thanks a lot!

> **duanedesign said:**
> If  you see <local machine> it means you have deleted all your machines from your computer, but there is still a Token in the keyring. Please try the following.

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open System-> Preferences-> Ubuntu One (or Me Menu ->
       Ubuntu One)
   9. a web page should open, prompting you to add your computer to
       your Ubuntu One account
  10. Add your computer

Please let us know if this helps.

thank you,
duanedesign

---

### Post by mdebusk on 2010-10-18
> **Ceezey77 said:**
> I'm running Ubuntu 10.04 - had the very same issue and ran the fix below.  Worked first time! Thanks a lot!

Still no joy here. Step nine in the "fix" (*a web page should open, prompting you to add your computer to your Ubuntu One account*) never happens.

---

### Post by rsouthard on 2010-10-19
Same here, browser window never opens.

---

### Post by Chris1274 on 2010-10-19
Likewise. I just installed Maverick on a ThinkPad T410. When I tried to hook it up to my Ubuntu One account, it went nowhere. The "connect" button is grayed out, and when I go to the Ubuntu One website, I don't see the option to "add this computer."

---

### Post by Chris1274 on 2010-10-19
Things seem to be working now. I deleted the Ubuntu One password and then stopped and restarted the sync-daemon. When I opened up u1 it showed that it was in the process of synchronizing.

I think what messed things up from the outset is that I had made Chromium my default browser. I guess u1 needs Firefox in order to set up properly?

---

### Post by Jacob111 on 2010-10-30
Hey guys, after fiddling with this for waaaayyyy too long, I finally found a solution.  I was having the same symptoms as so many others: You are told to open "password and encryption keys" and "delete the Ubuntu One entry", but there is no "Ubuntu One" entry to delete.

Sooooo, I found a folder called ~/.gnome2/keyrings.  Deleting that folder resets ALL saved passwords on programs associated with the gnome desktop.  For instance, after deleting, I had to re-enter my passwords in evolution mail, BUT it also made it so launching Ubuntu One prompted me to add an account.

I think there's a bug with U1 such that it's saved password doesn't show up in the keyring, even though an entry exists.  Deleting the keyring deletes it.  Hope this helps.

---

### Post by mdebusk on 2010-10-31
> **Chris1274 said:**
> The "connect" button is grayed out, and when I go to the Ubuntu One website, I don't see the option to "add this computer."

My "connect" button isn't grayed out, but when I press it, it turns gray and nothing happens afterward.

---

### Post by mdebusk on 2010-10-31
> **Chris1274 said:**
> I think what messed things up from the outset is that I had made Chromium my default browser. I guess u1 needs Firefox in order to set up properly?

Hmm... Firefox has always been my default browser.

---

### Post by LilleCarl on 2010-12-01
I did like this, uninstalled ubuntu one, then ran this:

```
u1sdtool -q; killall ubuntuone-login; u1sdtool -c
```

Then it where ready to go :)

---

### Post by duanedesign on 2010-12-01
On Maverick if you are having trouble adding your computer try the following steps. If you have already removed any Ubuntu One Tokens in the Keyring and still not getting the 'Add Computer' dialog, make sure you have tried Step 8.

1. Quit the Ubuntu One client
2. Open Applications->Accessories->Passwords and Encryption Keys
3. Click on the arrow next to "Passwords"
4. Right-click on the Ubuntu One token and select "Delete"
5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
6. Click on the checkbox next to your computer
7. Click the "Remove selected computers" button
8. killall ubuntu-sso-login; u1sdtool -q; u1sdtool -c
NOTE: (For Lucid): u1sdtool -q; killall ubuntuone-login; u1sdtool -c
9. a web page should open, prompting you to add your computer to
your Ubuntu One account
10. Add your computer

---

### Post by david.rahrer on 2010-12-04
I'm going to jump in as I'm having pretty much the same issue.  I noticed about a week ago that U1 had stopped working, i.e. my shared folders have no green check.  Preferences/UbuntuOne shows all it should except that connection status is "Unknown".  The sync daemon will not start.  It is listed correctly in the startup applications and I tried u1sdtool -s (it just sits there like it's hanging).  

I tried the steps listed above with no change.  It does come up and ask me to add my machine, which I do, all goes well except it doesn't start.  I even purged all U1 installs, rebooted and reinstalled, went through all the steps and have the same result.  The only thing I accomplished was removing the U1 section from my personal indicator applet menu (ME) under Broadcast Accounts.  

I can start another thread if necessary but it seems like the same stuff.  I'm eager for more suggestions as I've tried all I could find.  Thanks.

---

