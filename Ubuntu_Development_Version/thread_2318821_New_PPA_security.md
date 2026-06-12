---
title: "New PPA security?"
date: 2016-03-29
forum: Ubuntu Development Version
---

### Post by ELD on 2016-03-29
Couldn't find an answer anywhere else, since recently a bunch of PPA's have been giving warnings since Ubuntu is beefing up security.

I mentioned it to the SimpleScreenRecorder dev who said:
> [COLOR=#333333][FONT=Helvetica Neue]As far as I know that's not my key. I only sign the [/FONT][/COLOR][source package]("https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder/+files/simplescreenrecorder_0.3.6+1~ppa1~xenial1.dsc")[COLOR=#333333][FONT=Helvetica Neue], and that one is actually signed with SHA256. What am I supposed to do to change the other signatures?[/FONT][/COLOR]

Is it up to each PPA owner, or Canonical who run Launchpad to sort the new security stuff? I couldn't find any guide on the new measures to let them know.

---

### Post by QDR06VV9 on 2016-03-29
They know now
[URL="https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331"]https://bugs.launchpad.net/ubuntu/+s...t/+bug/1558331

[/URL][https://juliank.wordpress.com/2016/0...s-on-apt-sha1/]("https://juliank.wordpress.com/2016/03/15/clarifications-and-updates-on-apt-sha1/")[URL="https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331"]
[/URL]

---

### Post by grahammechanical on 2016-03-29
I read the bug report and I just had to laugh.

Ask people to volunteer to trawl through all the PPAs in Launchpad to find out which ones were throwing up a certain error message and hardly anybody would volunteer. But, in a bug report ask people to stop reporting PPAs throwing up the certain error message because the problem in known & being fixed and people carry on posting lists of PPAs throwing out the error message.

Then someone says the bug has been fixed and some else says, no it isn't. I am still getting the error messages. The bug report was about a comma in the error message whose placement gave the message more than one meaning. That was fixed. The bug report was not about stopping the error message. That will only happen when the PPA is resigned by a stronger algorithm. And if that does not happen by next year the PPA will be broken and should be considered a security risk.

I wonder if the error message that was thrown up on 64 bit installations of Chrome when Google dropped support for 32 bit Chrome is getting mixed up in all of this.

Regards.

---

### Post by PaulW2U on 2016-03-29
> **runrickus said:**
> They know now
[https://bugs.launchpad.net/ubuntu/+s...t/+bug/1558331]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331")
I think that bug report shows that many users are running a development version of Ubuntu without fully understanding that their experience of doing so may not be what they expected.

It's a shame that a Launchpad bug report is turned into something that resembles a mailing list discussion because some of the bug subscribers cannot be bothered to read what Colin Watson and others have written. May be Launchpad needs a "no more comment" mode to stop pointless comments being added to a bug report where **any** further comments would serve no useful purpose?.

---

### Post by QDR06VV9 on 2016-03-29
> **PaulW2U said:**
> I think that bug report shows that many users are running a development version of Ubuntu without fully understanding that their experience of doing so may not be what they expected.

It's a shame that a Launchpad bug report is turned into something that resembles a mailing list discussion because some of the bug subscribers cannot be bothered to read _**what Colin Watson and others have written. May be Launchpad needs a "no more comment" mode to stop pointless comments being added to a bug report where any further comments would serve no useful purpose?.**_
Could not agree more..it really is a pity.

---

### Post by sammiev on 2016-03-29
> **PaulW2U said:**
> I think that bug report shows that many users are running a development version of Ubuntu without fully understanding that their experience of doing so may not be what they expected.

It's a shame that a Launchpad bug report is turned into something that resembles a mailing list discussion because some of the bug subscribers cannot be bothered to read what Colin Watson and others have written. May be Launchpad needs a "no more comment" mode to stop pointless comments being added to a bug report where **any** further comments would serve no useful purpose?.

Read what?

---

### Post by PaulW2U on 2016-03-29
> **sammiev said:**
> Read what?
Colin Watson has said several times that the "error" messages are just warnings and that apt is working as intended. The fix is to update Launchpad but several users keep complaining and say that the bug in apt has not been fixed. The error messages will only go away when Launchpad has been updated by Canonical IS which I thought was going to be today.

See [bug #1556666]("https://bugs.launchpad.net/launchpad/+bug/1556666") for the real issue.

---

### Post by sammiev on 2016-03-29
> **PaulW2U said:**
> Colin Watson has said several times that the "error" messages are just warnings and that apt is working as intended. The fix is to update Launchpad but several users keep complaining and say that the bug in apt has not been fixed. The error messages will only go away when Launchpad has been updated by Canonical IS which I thought was going to be today.

See [bug #1556666]("https://bugs.launchpad.net/launchpad/+bug/1556666") for the real issue.

Sorry Paul,

I meant that as a joke...

I seen the bug report and couldn't believe what I was reading.

---

### Post by sudodus on 2016-03-29
Hi Paul,

Can you see, if [ppa:mkusb/ppa](https://launchpad.net/~mkusb/+archive/ubuntu/ppa) must upgrade the signing key?

---

### Post by QDR06VV9 on 2016-03-29
Well some got the fix, quite a chore for the many others..
> Colin Watson (cjwatson) wrote on 2016-03-27:     #10

[B]Easter status: didn't entirely make it before the holidays, but the necessary code is deployed and a ticket is in our sysadmins' hands with full instructions on re-signing all xenial PPAs.
[/B]

Colin Watson (cjwatson) wrote 9 hours ago:     #13

@mc3man: _**No, it's only fixed for those PPAs that have had any xenial publications in the last week or so.**_EDIT @ sudodus I did not get a warning for your PPA

---

### Post by PaulW2U on 2016-03-29
> **sudodus said:**
> Can you see, if [ppa:mkusb/ppa](https://launchpad.net/~mkusb/+archive/ubuntu/ppa) must upgrade the signing key?
My current warnings when running an update in Xenial are:
```

W: http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg: Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu/dists/xenial/InRelease: Signature by key 2014A4CC6F1D82F0C47ECEB8978228591BD3A65C uses weak digest algorithm (SHA1)
W: http://ppa.launchpad.net/gwendal-lebihan-dev/hexchat-stable/ubuntu/dists/xenial/InRelease: Signature by key 109C2938F84496D6ACB6D805A777609328949509 uses weak digest algorithm (SHA1)
[COLOR="#FF0000"]W: http://ppa.launchpad.net/mkusb/ppa/ubuntu/dists/xenial/InRelease: Signature by key 29D76ADA2D15A87BF4C68B823729827454B8C8AC uses weak digest algorithm (SHA1)[/COLOR]
W: http://ppa.launchpad.net/gezakovacs/ppa/ubuntu/dists/wily/Release.gpg: Signature by key BCCCC1E2835433FA7DB85D51D45DF2E8FC91AE7E uses weak digest algorithm (SHA1)
W: http://www.tataranovich.com/debian/dists/wily/Release.gpg: Signature by key 4A49274193083320450B7E4D836CC41976FB442E uses weak digest algorithm (SHA1)
W: https://weechat.org/ubuntu/dists/xenial/InRelease: Signature by key 11E9DE8848F2B65222AA75B8D1820DB22A11534E uses weak digest algorithm (SHA1)

```

---

### Post by grahammechanical on 2016-03-29
Some of those users were complaining that PPAs were broken. Were they trying to install in Xenial Xerus software from a PPA that did not exist for Xenial? That would not only throw up the warning about weak encryption keys but also a failed to fetch message. 

Example:

> A bunch of warnings should not result in an error (E: Some index files  failed to download. They have been ignored, or old ones used instead.)  and it should totally NOT tell non technical users to "Check their  Internet connection"! SHA1 was OK for a good number of years amd all of a sudden, it becomes so insecure that it should break user's installs?

Followed by this admission

> Turns out that the issue is not as bad as I thought it was. The error  message was due to a single repo and not all the repos showing warnings.  Removing it got rid of the error message in both the terminal and the  GUI updater. The affected repo was the Google Talk Plugin:

So, that complaint was irrelevant to the issue. It all adds "noise" to a bug report. And no apology for the rant.

By Colin Watson

> You do not need to do anything if you have your own PPA.  Furthermore,  people do not need to keep reporting individual PPAs that are signed  with weak digests.  We'll fix them in bulk, hopefully quite soon (still  working on the last bits of code for that).

But they did keep on reporting. Yes, sad for the developers.

---

### Post by sudodus on 2016-03-29
I hope that there will be a document that describes how to do it. If you find it, please link to it in this thread :-P

I normally upload new versions to the unstable ppa, [ppa:mkusb/unstable](https://launchpad.net/~mkusb/+archive/ubuntu/unstable) and after a period of testing I copy it to the stable ppa, ppa:mkusb/ppa.

I added both ppa versions to a live session, and updated. I get the warning for ppa:mkusb/ppa but not for ppa:mkusb/unstable. I hope it means that the signature is OK in the unstable ppa. So Colin Watson did something with PPAs that have new content, and ppa:mkusb/unstable has new content (mkusb 10.6). I hope it is a persistent change.

1. Will the signature quality survive for new uploads in the unstable ppa, or must I change my signing key?

2. Will the signature survive copying to the stable ppa with the packages? I will find out, when I do it after a couple of weeks.

-o-

Maybe you have the unstable ppa, *runrickus* :-)

---

### Post by mc4man on 2016-03-29
> **sudodus said:**
> I hope that there will be a document that describes how to do it. If you find it, please link to it in this thread :-P

I normally upload new versions to the unstable ppa, [ppa:mkusb/unstable](https://launchpad.net/~mkusb/+archive/ubuntu/unstable) and after a period of testing I copy it to the stable ppa, ppa:mkusb/ppa.

I added both ppa versions to a live session, and updated. I get the warning for ppa:mkusb/ppa but not for ppa:mkusb/unstable. I hope it means that the signature is OK in the unstable ppa. So Colin Watson did something with PPAs that have new content, and ppa:mkusb/unstable has new content (mkusb 10.6). I hope it is a persistent change.

1. Will the signature quality survive for new uploads in the unstable ppa, or must I change my signing key?

2. Will the signature survive copying to the stable ppa with the packages? I will find out, when I do it after a couple of weeks.

-o-

Maybe you have the unstable ppa, *runrickus* :-)

No one will need to do anything. Currently any xenial ppa that gets new builds will get the new signing whatever. 
In the very near future all xenial ppa's with existing/prior builds will also be signed with whatever

---

### Post by QDR06VV9 on 2016-03-29
> **sudodus said:**
> 
Maybe you have the unstable ppa, *runrickus* :-)
Yes Sir that is the one...:D After all this is the testing area...LOL
Thanks Paul for pointing to the other PPA Stable Warning.

---

### Post by sudodus on 2016-03-29
Thanks everybody :-)

Now I know, that I need not spam those two bug reports at Launchpad. And I hope this thread will reassure many other people too ;-)

---

### Post by PaulW2U on 2016-03-30
In [bug report #1558331]("https://bugs.launchpad.net/bugs/1558331") Colin Watson said:
> As per my most recent comment on bug 1556666, this is now fixed for all
xenial Release files in PPAs.  Pre-xenial Release files are less
important numerically for this, but we know that some people have them
enabled on xenial systems, so we'll be re-signing those too over the
coming weeks.
I'm certainly seeing less warnings now and **all** that I do see are for non-Launchpad PPAs which are obviously outside of Colin's control.

---

### Post by grahammechanical on 2016-03-30
Job done for Xenial

[http://www.chiark.greenend.org.uk/~cjwatson/blog/re-signing-ppas.html](http://www.chiark.greenend.org.uk/~cjwatson/blog/re-signing-ppas.html)

Well done and thank you Colin Watson

---

### Post by QDR06VV9 on 2016-03-30
> **grahammechanical said:**
> Job done for Xenial

[http://www.chiark.greenend.org.uk/~cjwatson/blog/re-signing-ppas.html](http://www.chiark.greenend.org.uk/~cjwatson/blog/re-signing-ppas.html)

Well done and thank you Colin Watson
+1 This gentleman has exercised great patience and professional regard through all of this.
Very much appreciated Colin Watson :KS.

---

### Post by sudodus on 2016-03-30
> **runrickus said:**
> +1 This gentleman has exercised great patience and professional regard through all of this.
Very much appreciated Colin Watson :KS.

+1 :-)

---

