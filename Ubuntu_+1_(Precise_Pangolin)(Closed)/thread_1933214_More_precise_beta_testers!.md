---
title: "More precise beta testers!"
date: 2012-02-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ptn107 on 2012-02-28
If you have some spare time it would be appreciated!  Do as many testcases on a spare machine as possible.  Not your main pc please as these are still pre-release and may break.  Please try not to do these on a VM, that's not as helpful as real hardware.

[_http://iso.qa.ubuntu.com/qatracker/milestones/208/builds_]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds")

---

### Post by matt_symes on 2012-02-28
I can tackle some tomorrow night if needed.

Do i need to sign up to any group to help out ? What's the basic process ?

Which download do i need ?

---

### Post by ptn107 on 2012-02-28
You need an open id: [_http://openid.net/_]("http://openid.net/") account.  If you can login to launchpad.net then you already have one.

Just pick a build from the list you are willing to test:
[_http://iso.qa.ubuntu.com/qatracker/milestones/208/builds_]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds")

Under each build you should choose whatever testcase you are willing to try.  In each testcase you can click 'Link to the testcase' for details on how to run the test.

The cdrom icon with the green arrow is a quick link to downloading the appropriate iso image for that build/testcase.

---

### Post by Irihapeti on 2012-02-29
I'd be pleased to do more, but nearly all of them require something other than manual partitioning.

I've got spare partitions but not spare drives. Are any compromises allowed? e.g. manual partitioning for Free Software installs?

---

### Post by matt_symes on 2012-02-29
> **ptn107 said:**
> You need an open id: [_http://openid.net/_]("http://openid.net/") account.  If you can login to launchpad.net then you already have one.

Just pick a build from the list you are willing to test:
[_http://iso.qa.ubuntu.com/qatracker/milestones/208/builds_]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds")

Under each build you should choose whatever testcase you are willing to try.  In each testcase you can click 'Link to the testcase' for details on how to run the test.

The cdrom icon with the green arrow is a quick link to downloading the appropriate iso image for that build/testcase.

Thanks for the info. I will start testing as soon as i can.

---

### Post by Yellow Pasque on 2012-02-29
> **ptn107 said:**
> Please try not to do these on a VM, that's not as helpful as real hardware.

There's still a lot that can be tested on a VM, and it's much better than not testing at all..

---

### Post by kansasnoob on 2012-02-29
> **Temüjin said:**
> There's still a lot that can be tested on a VM, and it's much better than not testing at all..

All testing is always welcome :D

Different testers look at different things. I've had a bug up my butt since they changed ubiquity in Maverick so thats been my greatest focus since then.

Other testers will focus on different processes/apps so no testing is wasted. I've spent a lot of time chasing my own tail a few times but it's never wasted time because it's always a learning experience :D

---

### Post by jerrylamos on 2012-02-29
> **ptn107 said:**
> If you have some spare time it would be appreciated!  Do as many testcases on a spare machine as possible.  Not your main pc please as these are still pre-release and may break.  Please try not to do these on a VM, that's not as helpful as real hardware.

[_http://iso.qa.ubuntu.com/qatracker/milestones/208/builds_]("http://iso.qa.ubuntu.com/qatracker/milestones/208/builds")

?  Beta is out March 26 ?  I've got test machines which I install precise on from time to time and update - but that's post Alpha 2, not "precise beta".

?

Jerry

---

### Post by balloons on 2012-02-29
Yes! the biggest piece to helping with iso testing is just hopping on the #ubuntu-testing channel and letting people now you want to help test. They are helpful and will point things out to you and walk you thru everything. I don't have spare hardware, so I test in VM's -- it's still important and useful to do so.

Check out this wiki page as well.

[https://wiki.ubuntu.com/Testing/ISO](https://wiki.ubuntu.com/Testing/ISO)

---

### Post by matt_symes on 2012-02-29
> **guitara said:**
> Yes! the biggest piece to helping with iso testing is just hopping on the #ubuntu-testing channel and letting people now you want to help test. They are helpful and will point things out to you and walk you thru everything. I don't have spare hardware, so I test in VM's -- it's still important and useful to do so.

Check out this wiki page as well.

[https://wiki.ubuntu.com/Testing/ISO](https://wiki.ubuntu.com/Testing/ISO)

Thanks for this as well.

---

### Post by nm_geo on 2012-02-29
> **kansasnoob said:**
> All testing is always welcome :D

Different testers look at different things. I've had a bug up my butt since they changed ubiquity in Maverick so thats been my greatest focus since then.

Other testers will focus on different processes/apps so no testing is wasted. I've spent a lot of time chasing my own tail a few times but it's never wasted time because it's always a learning experience :D

What was that bug number on launchpad?  LOL and where is it located .... 
I will try to get some more in tonight on the Lubuntu desktop amd64 isos.. Finish that jewel off maybe.

---

### Post by dcstar on 2012-03-01
And here was me worried that there were too many imprecise beta testers....

---

### Post by pinguinhood on 2012-03-01
I'm waiting for my new notebook, than I will try!
Thanks for the info!

---

### Post by Doug S on 2012-03-01
When entering test results, there is a box called "Hardware Profile" with an under comment "URL to hardware profile". What is expected for that box? Is there an example or instructions to work from?
 
Is my interpretation of the colour coding scheme on the summary page correct?
Blue = tests not complete, but no problems found, so far
Green = all tests complete, at least once, and all O.K.
Light red = some problem found
Darker red or purple = some problem and bug link provided

---

### Post by Irihapeti on 2012-03-01
The hardware profile thing is a bit of a mystery to me, too.

Sometimes I link to a bug attachment - output of lspci -vvnn. But I think that it would be helpful if we could attach hardware profiles to a clearly defined place. Maybe as part of one's QA website or Launchpad profile, for example.

---

### Post by nm_geo on 2012-03-01
Here are a few ideas.  You can link to a google document.. You can link to a public dropbox file.. I think you could link to a UbuntuOne public file. Any file in the cloud..

Sometimes when testing, I insert the link to hardware info from a google document that is read only for the public.

Of course just giving a brief description in comments can be helpful. 

Main thing is.. we really do need as many testers as possible especially right before alpha and beta release days.

---

### Post by Doug S on 2012-03-02
O.K., I guessed at what might be wanted for the hardware profile information, made a web page containing that information and edited my test results to add the URL.

---

### Post by jerrylamos on 2012-03-08
Ubiquity won't run on this Acer Aspire one netbook.

Launchpad Bug #950167

Selecting the installer from the launcher the icon quivers a while then nothing happens.

cli install gets this:

ubuntu@ubuntu:~$ sudo ubiquity
Inhibit all polling failed: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

again nothing happens.

I tried to enter something on the QA but don't know how.

BTW, making this entry from Beta Live all updated & upgraded, live runs fine except for ubiquity.

Jerry

---

### Post by fjgaude on 2012-03-08
I've reported each error or issue that has come up. My main system has been pretty well taken care of with most errors already having been reported.

Only remaining bug is machine will not come out of Suspend, an ACPI issue with Z68 chipsets.

This 12.04 LTS is going to be the best distro ever.

---

### Post by balloons on 2012-03-08
> **jerrylamos said:**
> Ubiquity won't run on this Acer Aspire one netbook.

Launchpad Bug #950167

Selecting the installer from the launcher the icon quivers a while then nothing happens.

cli install gets this:

ubuntu@ubuntu:~$ sudo ubiquity
Inhibit all polling failed: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

again nothing happens.

I tried to enter something on the QA but don't know how.

BTW, making this entry from Beta Live all updated & upgraded, live runs fine except for ubiquity.

Jerry


Jerry, you can submit a bug for this (please do!) by typing 'ubuntu-bug ubiquity' on the command line. Ubiquity gets a lot of attention and we need to know about breakages. This is one of those packages that causes re-work and respins.. We definitely want to avoid those if possible. Thanks for finding and reporting it!

---

### Post by jerrylamos on 2012-03-08
> **guitara said:**
> Jerry, you can submit a bug for this (please do!) by typing 'ubuntu-bug ubiquity' on the command line. Ubiquity gets a lot of attention and we need to know about breakages. This is one of those packages that causes re-work and respins.. We definitely want to avoid those if possible. Thanks for finding and reporting it!

Finally got a bug entered, it's #950167.

'ubuntu-bug ubiquity' results in:

> The problem cannot be reported:

This is not an official Ubuntu package. Please remove any third party package and try again.

So I put a bunch of info in the bug report I don't know if anything else would be of use.  No reply yet.

Could probably enter a launchpad bug that "ubuntu-bug ubiquity" doesn't work but I'm more inteested in getting the Beta installed.  Maybe something like "ubuntu-bug ubuntu-bug" I seriously doubt that would work.

Thanks, Jerry

---

### Post by cariboo on 2012-03-08
> **jerrylamos said:**
> Finally got a bug entered, it's #950167.

'ubuntu-bug ubiquity' results in:



So I put a bunch of info in the bug report I don't know if anything else would be of use.  No reply yet.

Could probably enter a launchpad bug that "ubuntu-bug ubiquity" doesn't work but I'm more inteested in getting the Beta installed.  Maybe something like "ubuntu-bug ubuntu-bug" I seriously doubt that would work.

Thanks, Jerry

You should have reported the bug using the Live CD, or iso image.

---

### Post by manzdagratiano on 2012-03-08
BRILLIANT!

I decided to say <snip> it and upgraded from Oneiric to Precise... and I must say, Precise both looks AND feels awesome! Upgrade went smooth (Dell Vostro V13) and an equally smooth reboot to an awesome looking LightDM, and an awesome desktop.

The new Unity is excellent! I REALLY appreciate the fact that some minor annoyances have been done away with - like if I had Firefox open, when I would go to hit the back button, the launcher would appear in Oneiric, but now the Launcher occupies its own space, with no interference. The HUD is as cool as I imagined, and though there is more to be desired, it more than impresses!

No errors whatsoever so fa, and things feel snappy... Since Oneiric and I have had a somewhat bumpy relationship (though I loved how it looked, it never felt quite right), I am looking forward to enjoying all of Precise. I think the real deal for me would be when I upgrade my other machine - a VAIO VGNAR520E which has an nvidia card, and is usually on like a server most of the time... That should let me see how Precise handles memory over longer periods of time.

---

### Post by jerrylamos on 2012-03-09
> **cariboo907 said:**
> You should have reported the bug using the Live CD, or iso image.

I was running iso image.  ubuntu-bug didn't work as in my post and as in launchpad bug #950167.

Any other ideas? 

Thanks, Jerry

---

### Post by linux6994 on 2012-03-09
My Precise desktop is rocking! All looking good except sparse file not found error on boot, but it boots just fine anyway :)

---

### Post by balloons on 2012-03-09
> **jerrylamos said:**
> I was running iso image.  ubuntu-bug didn't work as in my post and as in launchpad bug #950167.

Any other ideas? 

Thanks, Jerry

Did you have any third-party ppa's installed? If you download and run the latest iso and get this error and your not adding anything, it's definitely a bug in apport. Apport gives that error if for some reason your running a non-standard version of a package, and then they don't want to get bugs against it as it's something you changed.

---

### Post by dino99 on 2012-03-09
> **jerrylamos said:**
> I was running iso image.  ubuntu-bug didn't work as in my post and as in launchpad bug #950167.

Any other ideas? 

Thanks, Jerry

do it via  [https://launchpad.net/ubuntu/+source/ubiquity](https://launchpad.net/ubuntu/+source/ubiquity)   --> Report a bug (on top right side)

---

### Post by manzdagratiano on 2012-03-09
Okay... I **MUST** proclaim how **PHENOMENAL** this release is going to be.

I was upgrading my VAIO, which has always been the source of unexpected problems and therefore also of much learning.

The worst happened - **the upgrade got interrupted** because I decided to plug in an external drive during the upgrade and when the drive folder popped up in nautilus, unity seemed to crash (still oneiric).

Logging in from a virtual console, I saw that update-manager was still running. I let it run for a while and then checked that the new kernel had been installed, and the grub menu had been updated. I decided to take the plunge and issues a `sudo pkill X' to see if anything could be salvaged - and the result was a broken LightDM. So I **rebooted, into recovery mode**, assuming the worst and prepated to run things of the effect of `sudo dpkg --configure -a'. I chose the `dpkg' option from the menu.

And well folks... dpkg fixed all the packages that had to be configured, and even removed all of the obsoleted packages. The result: a **beautiful fully functional Precise desktop**!

And I am typing from there as we speak... I am floored!

---

