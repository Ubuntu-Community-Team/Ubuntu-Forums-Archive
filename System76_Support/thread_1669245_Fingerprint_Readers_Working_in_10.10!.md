---
title: "Fingerprint Readers Working in 10.10!"
date: 2011-01-17
forum: System76 Support
---

### Post by thomasaaron on 2011-01-17
ANNOUNCEMENT!

Integrated fingerprint readers now work on all System76 machines running Ubuntu 10.10!

Full instructions are [here]("http://knowledge76.com/index.php/Fingerprint_Reader_Usage").

---

### Post by tersogar on 2011-01-18
Works perfect, even in Lucid. Thanks System76.

---

### Post by Cygnia on 2011-01-19
It doesn't work for me on my PanP4n running Maverick. It accepts my fingerprint with a check mark and "OK", but then nothing happens for several minutes (the "Next" button is grayed out.) Then a dialog pops up with the message that the fingerprint wasn't saved.

---

### Post by Cygnia on 2011-01-19
It doesn't work for me on my PanP4n running Maverick. It accepts my fingerprint with a check mark and "OK", but then nothing happens for several minutes (the "Next" button is grayed out.) Then a dialog pops up with the message that the fingerprint wasn't saved.

---

### Post by Cygnia on 2011-01-19
It doesn't work for me on my PanP4n running Maverick. It accepts my fingerprint with a check mark and "OK", but then nothing happens for several minutes (the "Next" button is grayed out.) Then a dialog pops up with the message that the fingerprint wasn't saved.

---

### Post by Cygnia on 2011-01-19
It doesn't work for me on my PanP4n running Maverick. It accepts my fingerprint with a check mark and "OK", but then nothing happens for several minutes (the "Next" button is grayed out.) Then a dialog pops up with the message that the fingerprint wasn't saved.

---

### Post by HotShotDJ on 2011-01-19
> **Cygnia said:**
> It doesn't work for me on my PanP4n running Maverick. It accepts my fingerprint with a check mark and "OK", but then nothing happens for several minutes (the "Next" button is grayed out.) Then a dialog pops up with the message that the fingerprint wasn't saved.It should be asking you to swipe your finger again.  For me, it asked 3 times (each time giving the check mark and "OK.").  It works perfectly on my PanP5.

---

### Post by tschlemmer on 2011-01-19
I have 10.10 installed on my panp5 laptop and while I can successfully scan my fingerprint and save it on the disk still have to enter my password for "sudo" commands.

---

### Post by isantop on 2011-01-20
Have you logged out and logged back in? If not, that's what's holding you back.

---

### Post by pafufta503 on 2011-01-20
It works for me too.  I swipe my finger, it logs my user in, but then I get a dialog that says "Enter password to unlock login keyring".  Then I enter my password.  It is mildly redundant, I would like to finger swipe to login and not have to enter my password.

---

### Post by marshmallow1304 on 2011-01-20
It looks like it should work, but when I try to scan in a fingerprint I get 5 OKs across the board followed by a "Fingerprint failed" dialog.

Also, if anyone else happens to be using Gentoo, there's a preliminary ebuild available [here]("https://bugs.gentoo.org/show_bug.cgi?id=341105").

---

### Post by isantop on 2011-01-21
Can you please open a terminal and run this command:
```
lsusb
```

Send me the output.

---

### Post by tschlemmer on 2011-01-22
> **isantop said:**
> Have you logged out and logged back in? If not, that's what's holding you back.
When I lock the screen the I can ether enter my password or it has a animated graphic showing that I can swipe my finger.  When I swipe my fingerprint it just sits there saying "ready..." and doesn't do anything. I have logged out and back in numerous times as well.

---

### Post by HotShotDJ on 2011-01-22
> **pafufta503 said:**
> It works for me too.  I swipe my finger, it logs my user in, but then I get a dialog that says "Enter password to unlock login keyring".  Then I enter my password.  It is mildly redundant, I would like to finger swipe to login and not have to enter my password.This is because, for technical reasons, using your fingerprint to login does not unlock the gnome-keyring.  See: [http://www.n-view.net/Appliance/fingerprint/doc/Manual_en.html](http://www.n-view.net/Appliance/fingerprint/doc/Manual_en.html)> If you use fingerprints for log-on to your system, no password is entered, since you were detected on the basis of your fingerprint. Depending on the configuration of your system a password might be needed to decrypt important data. For example this is the case if your home directory or the gnome-keyring is encrypted with your login password.

---

### Post by marshmallow1304 on 2011-01-23
Relevant output from lsusb:

```
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
```

---

### Post by IAmWhatWasDavidBowman on 2011-01-23
I get the fingerprint not saved message on my PanP7. I tried removing it, but no luck. 

```
Bus 002 Device 004: ID 147e:1000 Upek 

sudo apt-get remove fingerprint-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libbonoboui2-0: Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
E: Broken packages

```

---

### Post by pafufta503 on 2011-01-27
> **HotShotDJ said:**
> This is because, for technical reasons, using your fingerprint to login does not unlock the gnome-keyring.  See: [http://www.n-view.net/Appliance/fingerprint/doc/Manual_en.html](http://www.n-view.net/Appliance/fingerprint/doc/Manual_en.html)KDE would not have this problem?  once i enter my password i can fingerswipe for anything, screensavers, terminal sudo, synaptic, etc.  it's pretty smooth, i just hope noone takes a mold of my fingerprint while i am sleeping, or worse cut my finger off to gain access to my computer!  this is some serious james bond technology, i am really enjoying this feature.

---

### Post by HotShotDJ on 2011-01-27
> **pafufta503 said:**
> KDE would not have this problem?I don't know how these issues are handled under KDE.  I only have one computer with KDE installed and it doesn't have a fingerprint reader, so I haven't looked into any issues that may or may not be present with fingerprint-gui under KDE.

---

### Post by hamstap85 on 2011-01-29
> **thomasaaron said:**
> ANNOUNCEMENT!

Integrated fingerprint readers now work on all System76 machines running Ubuntu 10.10!

Full instructions are [here]("http://knowledge76.com/index.php/Fingerprint_Reader_Usage").
On my panp7, before I followed the instructions, Fingerprint GUI was installed (didn't catch the version# unfortunately), but when I would go to the Scan/Verify tab, it would immediately raise an error message box without waiting any time at all, that said:

Could not open fingerprint device.
Permission problem?

Now that I did the process, it goes to the tab, and I have time to swipe my finger, however after about a second, it goes back to the first tab and displays the same error message. What the hell is going on!!?

---

### Post by IAmWhatWasDavidBowman on 2011-01-30
> **hamstap85 said:**
> On my panp7, before I followed the instructions, Fingerprint GUI was installed (didn't catch the version# unfortunately), but when I would go to the Scan/Verify tab, it would immediately raise an error message box without waiting any time at all, that said:

Could not open fingerprint device.
Permission problem?

Now that I did the process, it goes to the tab, and I have time to swipe my finger, however after about a second, it goes back to the first tab and displays the same error message. What the hell is going on!!?

I've seen the same thing. I actually have two different Fingerprint GUI icons in my System > Preferences menu. The two different commands that are initiated are:

"fingerprint-gui debug" - gives that "Permission problem" message
"fingerprintGUI --debug" - just doesn't work for me. Won't save the fingerprint.

I should mention that I'm on Lucid.

---

### Post by isantop on 2011-01-31
Have you guys tried installing Fingerprint Reader support before? If so, you'll want to completely remove everything from both attempts, then try again, as some files may be conflicting with each other.

---

### Post by IAmWhatWasDavidBowman on 2011-02-03
> **isantop said:**
> Have you guys tried installing Fingerprint Reader support before? If so, you'll want to completely remove everything from both attempts, then try again, as some files may be conflicting with each other.

Hey isantop. Thanks for the suggestion. I did have the Fingerprint Reader support installed before. I see two menu entries for the GUI. Since they specified different executables, I tried removing both. This is what I get when I try to remove them:

```
phil@tux:~$ sudo apt-get remove fingerprint-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libbonoboui2-0: Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
E: Broken packages
phil@tux:~$ sudo apt-get remove fingerprintGUI
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fingerprintGUI

```

As you can see from the terminal output, the second package says it doesn't exist, but both menu entries will launch the Fingerprint Reader GUI.

Any advice you could offer is appreciated!

---

### Post by tschlemmer on 2011-02-06
> **HotShotDJ said:**
> This is because, for technical reasons, using your fingerprint to login does not unlock the gnome-keyring.  See: [http://www.n-view.net/Appliance/fingerprint/doc/Manual_en.html](http://www.n-view.net/Appliance/fingerprint/doc/Manual_en.html)

What I did was the following:

1) uninstall the fingerprint-gui
2) sudo pam-auth-update --force
3) Reinstalled the fingerprint-gui package
4) Rescanned my fingerprint.

It is working now. When I lock the screen I simply need to swipe my finger to unlock the screen now. I believe the issue was solved due to me running the "pam-auth-update --force" command first before reinstalling the package.

---

### Post by IAmWhatWasDavidBowman on 2011-02-18
I would try this, but I can't even get step 1 to work for me. isantop?

---

### Post by isantop on 2011-02-18
Here's the instructions you followed to install the fingerprint reader software:

[http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation)

So, you'll want to:

Create a working directory:

```
mkdir fpreader
cd fpreader
```

Revert the Pam changes
```
sudo cp /etc/pam.d/common-auth_orig
```

Remove Fprint Demo
```
wget http://projects.reactivated.net/snapshots/fprint_demo/fprint_demo-20080319-5d86c3f7.tar.bz2
tar xjf fprint_demo-20080319-5d86c3f7.tar.bz2
cd fprint_demo-20080319-5d86c3f7/
sh autogen.sh
./configure --prefix=/usr
make
sudo make uninstall
cd ..
```

Remove pam_fprint
```
wget http://projects.reactivated.net/snapshots/pam_fprint/pam_fprint-20080330-5452ea09.tar.bz2
tar xjf pam_fprint-20080330-5452ea09.tar.bz2
cd pam_fprint-20080330-5452ea09/
sh autogen.sh
./configure --prefix=/usr
make
sudo make uninstall
cd ..
```

Remove fprint
```
wget http://projects.reactivated.net/snapshots/libfprint/libfprint-20080810-6b8b17f5.tar.bz2
tar xjf libfprint-20080810-6b8b17f5.tar.bz2
cd libfprint-20080810-6b8b17f5/
sh autogen.sh
./configure --prefix=/usr
make
sudo make uninstall
cd ..
```

Remove libusb
```
wget http://downloads.sourceforge.net/libusb/libusb-0.9.2.tar.bz2?modtime=1216505974&big_mirror=0
tar xjf libusb-0.9.2.tar.bz2
cd libusb-0.9.2/
./configure --prefix=/usr
make
sudo make uninstall
cd ..
```

Then give it a try.

---

### Post by IAmWhatWasDavidBowman on 2011-02-23
isantop,

I tried waiting several days to see if the site would come back up, but the [http://projects.reactivated.net](http://projects.reactivated.net) domain seems to be down.

Can you possibly point me to a mirror?

Thanks again,

Dave

---

### Post by janlan on 2011-02-23
I have Lenovo Ideapad v460 but my fingerprint scanner is not listed in Fingerprint GUI. Can someone help?

---

### Post by isantop on 2011-02-23
@janlan: This fix is for System76 computers only. While I'm not saying it definitely won't work on other systems, we don't test with them, and obviously can't support them. You may want to try posting your question in the hardware sub-forum.

@IAmWhatWasDavidBowman: Unfortunately, I'm not sure if any exist. Do you still have the original working directory? If so, then you can use the files there. If not, I'm not sure where you can get them.

---

### Post by safira18 on 2011-02-25
> **Cygnia said:**
> It doesn't work for me on my PanP4n running Maverick. It accepts my fingerprint with a check mark and "OK", but then nothing happens for several minutes (the "Next" button is grayed out.) Then a dialog pops up with the message that the fingerprint wasn't saved.
I accept with information: It doesn't work for me on my PanP4n running Maverick. It accepts my  fingerprint with a check mark and "OK", but then nothing happens for  several minutes (the "Next" button is grayed out.) Then a dialog pops up  with the message that the fingerprint wasn't saved.

---

### Post by DedMoroz on 2011-03-02
So this will not work if the /home directory is encrypted? My sis has a Sys76 laptop with the fingerprint scanner. Now I would hate to tell her its not possible :|

---

### Post by isantop on 2011-03-03
It may not work with an encrypted /home, but it should be fine with an encrypted ~/Private folder. That's probably a better option anyway, as it makes recovering your files much easier in the event of a problem.

---

### Post by capitalfear on 2011-03-15
hasn't worked since i bought my pangolin...thanks, this will shave off an hour of my life by the time i die from entering my password

---

### Post by aranaea on 2011-03-25
> **DedMoroz said:**
> So this will not work if the /home directory is encrypted? My sis has a Sys76 laptop with the fingerprint scanner. Now I would hate to tell her its not possible :|

This works great on my Serval Pro.  In the fingerprint GUI you need to do the setup under the "Password" tab.  I put the encrypted password on a USB stick on my keychain and it's not asking me for my password at all.  Just swipe and go.

---

### Post by aranaea on 2011-04-29
I've just upgraded my serval pro to 11.04 and, while the fingerprint scanner still works for logging in, it no longer works when I launch an application that needs sudo access, like the Software Center.  It prompts for a password but it no longer prompts me to scan my finger print.  Anyone else having this issue?

---

### Post by isantop on 2011-04-29
This is a known issue, and we're working on getting it resolved. We should have a fix available soon, but in the meantime, I'd suggest removing the fingerprint reader support for now:

[http://knowledge76.com/index.php/Fingerprint_Reader_Usage#Removal](http://knowledge76.com/index.php/Fingerprint_Reader_Usage#Removal)

---

### Post by scarey9 on 2011-05-07
it works for everything except when i run sudo (or gksudo) in a terminal, otherwise no problems.

---

### Post by slavinzing56 on 2011-08-08
It doesn't work  for me on my PanP4n running Maverick. It accepts my fingerprint with a  check mark and "OK", but then nothing happens for several minutes (the  "Next" button is grayed out.) Then a dialog pops up with the message  that the fingerprint wasn't saved.

---

### Post by isantop on 2011-08-09
when you input your fingerprints, you need to swipe them in several times to give the system a chance to learn what they look like. Can you try swiping it again.

---

### Post by CaptSaltyJack on 2011-08-12
Does the fingerprint reader really not work with an encrypted home folder? Kind of a bummer.. any plans to address this? (if it's even possible)

---

### Post by aranaea on 2011-10-20
Is there a chance that the finger print reader will be working in 11.10 any time soon?

---

### Post by CaptSaltyJack on 2011-10-20
I'd like to hear an answer on this too. I have a problem with features being advertised that actually do not work. Not that I NEEDED a fingerprint reader, but still. If it was known to not work in Ubuntu 11.04, I don't think System76 should've advertised it on their site.

---

### Post by isantop on 2011-10-20
They were set to work in 11.10, but the changes to Gnome 3 broke a lot of the support for a bunch of PAM modules (Which is how the fingerprint readers work). We're working on getting them working now in 11.10, but it might be until 12.04 that we really get them working solidly.

---

