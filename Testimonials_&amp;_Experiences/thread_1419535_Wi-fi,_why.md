---
title: "Wi-fi, why?"
date: 2010-03-02
forum: Testimonials &amp; Experiences
---

### Post by Annoyed_User on 2010-03-02
After recently buying a Samsung netbook to replace my rapidly dying laptop, I decided to wipe the pre-installed XP that was chock-o-block full of trials and other pointless bloat that I couldn't be bothered to remove, and install UNR. 
This was a seriously bad idea.
When installing UNR, my internet was down, so sadly I missed a chance to save myself a lot of frustration. 
The nightmare basically unfolded like this. Upon booting UNR the day after installing it, I found that it didn't detect my Wi-fi connection. So I jacked in the ethernet cable, lspci'd in the Terminal, and spent the next 3 hours searching every corner of Google for guides/posts/threads that would tell me how I could get it to work. The only 2 threads I found that offered any kind of hope were on LinuxQuestions.org, and the English section of some obscure Polish distro. The  LinuxQuestions thread seemed hopeful, as it offered several possibilities, including dropping a firmware into /something/something/, but that just didn't work (and the more you read into the thread, the more you read of it working for some and not others). Then there was a very long post with a complicated explanation of how to modify the firmware to work, which was both way beyond my expertise, and later found to be wrong. And then a final solution that had a direct link to a driver for my Wi-fi chip, but unfortunately as I should have come to expect with linux, installing it was way too complex for me to understand. I have a basic understanding of the Terminal, but this was just too much.
To make things slightly worse, the thread on the Polish distro forum informed me (which after further reading on other sites has been confirmed) that actually my hardware IS supported by the kernel, but the process is broken as it misidentifies the chip, loads the wrong thing, which in turn doesn't work. It was at this point that I remembered about ndiswrapper. So after some more searching and post reading, I finally figured out how I install the driver (.inf). Amazingly it worked straight away. It even connected to a WPA2 network with no problem. So I thought my problems were finally over. But no, the connection would just randomly stop dead without disconnecting. The only way to make it work again was to restart the machine. At which point I just gave up.
It's sad that linux gets its *** handed to it over something as simple as a driver. In Windows this would be an hour long problem at most, but on linux in turns into a game breaker, which is just a huge disappointment.

So within the next week, I will be buying a USB DVD-Drive and a nice new copy of Win 7 Home. Pricey, but worth it if it saves me having to waste time like this again. I really doubt I'm the only user ubuntu and Linux has lost because of stupidly trivial issues like this, and I seriously doubt I will be the last!

---

### Post by ElSlunko on 2010-03-02
Since this isn't a forum for hardware support I wish you best of luck on your new OS choice!

---

### Post by pbpersson on 2010-03-02
> **Annoyed_User said:**
>  I really doubt I'm the only user ubuntu and Linux has lost because of stupidly trivial issues like this, but I seriously doubt I will be the last!

It does not sound trivial to me.....and I am certain that hardware support is the number one reason why people leave Linux.

When a new piece of hardware comes out, the creators of the hardware who know how it work are the ones who create the Windows drivers.  However, they:

1.  Have no interest in creating Linux drivers
2.  Do not want to give away any of the secrets that might help anyone create drivers

So the Linux geniuses create the drivers mostly through trial-and-error.

It is not a trivial problem, it is huge

---

### Post by bcbc on 2010-03-02
Just buy a USB wireless adaptor that's fully supported. For the future, you can boot ubuntu from the liveCD and try it before you wipe your native OS. (Or dual boot)

PS if you have recovery discs you should be able to restore XP, or get the shop that sold you the machine to get you one (you said it's new so shouldn't be an issue).

---

### Post by Jazzy_Jeff on 2010-03-02
Why don't you post a help thread on the forums here and see if anyone can help you? That would have been the first thing I did instead of complain that you could not figure it out by your self. A lot of times there is a simple fix to the problem.

---

### Post by Annoyed_User on 2010-03-02
> **bcbc said:**
> Just buy a USB wireless adaptor that's fully supported. For the future, you can boot ubuntu from the liveCD and try it before you wipe your native OS. (Or dual boot)

PS if you have recovery discs you should be able to restore XP, or get the shop that sold you the machine to get you one (you said it's new so shouldn't be an issue).

I don't want to spend extra money for something I already have! And as I said, my internet was down when I installed UNR.

---

### Post by ElSlunko on 2010-03-02
If my internet was down while installing a fresh copy of windows, I know most machines I own wouldn't have working wireless either 'till my internet popped up so I could snag the drivers from the manufacturer's website.

---

### Post by Annoyed_User on 2010-03-02
> **ElSlunko said:**
> If my internet was down while installing a fresh copy of windows, I know most machines I own wouldn't have working wireless either 'till my internet popped up so I could snag the drivers from the manufacturer's website.

You're kind of missing the point.

---

### Post by cariboo on 2010-03-02
I would suggest you start a thread [here]("http://ubuntuforums.org/forumdisplay.php?f=336") describing what wireless device you have, and what you have done so far to solve the problem. About the only wireless device people seem to be having problems with is some of the newer realtek chip-sets.

---

### Post by Annoyed_User on 2010-03-02
> **cariboo907 said:**
> I would suggest you start a thread [here]("http://ubuntuforums.org/forumdisplay.php?f=336") describing what wireless device you have, and what you have done so far to solve the problem. About the only wireless device people seem to be having problems with is some of the newer realtek chip-sets.

Thanks, but I have no interest in using ubuntu anymore. I only came back to clean up my original post.

---

### Post by howlingmadhowie on 2010-03-02
> **Annoyed_User said:**
> Thanks, but I have no interest in using ubuntu anymore. I only came back to clean up my original post.

This seems a bit counter-productive.  You buy hardware where the manufacturers probably go out of their way to make sure linux has great difficulty in supporting it, then you, someone with very little knowledge and experience of linux, spend hours searching the net for a driver and then you refuse offers of help when they come, preferring instead to spend your time creating an account and writing posts without any details about the problem you are having saying how terrible ubuntu is.

---

### Post by mastablasta on 2010-03-02
> **Annoyed_User said:**
> I don't want to spend extra money for something I already have! 
 
They are supposed to give it to you for free.
 
Also try it (since maybe you don't have CD you can instal LiveCD on USB key) before you install in on disk. If you dont' feel like trying and have enough disk space then dual boot to see if it all works.

---

### Post by Annoyed_User on 2010-03-02
> **howlingmadhowie said:**
> This seems a bit counter-productive.  You buy hardware where the manufacturers probably go out of their way to make sure linux has great difficulty in supporting it, then you, someone with very little knowledge and experience of linux, spend hours searching the net for a driver and then you refuse offers of help when they come, preferring instead to spend your time creating an account and writing posts without any details about the problem you are having saying how terrible ubuntu is.

I just posted my experience. I don't think ubuntu is terrible, but it is still too complex and time consuming to do something simple like install a driver. 
Anyway, as I have already said, I only came back to clean up my original post, not engage in a debate. Goodbye, and I hope you have more luck with ubuntu than I did! ^^

---

### Post by 3rdalbum on 2010-03-02
Sorry, I don't see the connection:

The right driver exists on your system, but the wrong driver captured the device. So you installed a Windows driver with Ndiswrapper.

To me, the first sentence suggests a trip to blacklist.conf to stop the wrong driver from loading.

You're complaining that "it's too difficult to install a driver"; but you already had the driver. Linux comes with drivers, Windows doesn't - you just needed about fifteen seconds to blacklist the incorrect driver.

I'll also add that you need to make sure that things are COMPATIBLE with eachother before jumping in and making a purchase. I was a Mac user for ten years, all Mac users were in the habit of checking compatibility before buying hardware. I would have thought that Vista's ABI bump would have put Windows users into the habit of checking compatibility before making a purchase.

And, you know, it's common sense in this day and age. You don't buy a 4WD and then complain because you can't use your old sedan tires on it. You don't buy an eSATA hard disk and then complain because it doesn't plug into your USB ports.

I just bought an Acer Aspire One - I literally didn't have to install a single driver. A bit of quick Googling on my part confirmed that this was a good netbook for me, and a quick test made sure that the battery from my old one was compatible with the new one.

If you want to try Windows 7, then go ahead. Enjoy it, but I hope you can get all the drivers you need. Use whatever is appropriate for you, but please don't tar Linux with the brush of "it's too hard".

---

### Post by M1ke on 2010-03-02
> **Annoyed_User said:**
> I don't want to spend extra money for something I already have!
 
...So next week you're going out to buy an Operating System? :-k
 
I am of course being facecious. Sorry it didn't work out for you, enjoy your new OS :)

---

### Post by armandh on 2010-03-02
too bad for annoyed user. enjoy 7

I now have a usb/dvd drive but before that I disassembled a usb/ide/hdd and plugged in a dvd drive for the loading process.

he could have used the savings for the 7!

my wifes laptop was tethered with a lan plug until the dreaded BCM-43xx WiFi's drivers finally arrived on the scene.

now slam dunk with OOTB Ubuntu.

---

### Post by ElSlunko on 2010-03-02
> **Annoyed_User said:**
> You're kind of missing the point.

Should you have another try at Ubuntu ask for help because your issue might get resolved & help many others facing the same problems. Enjoy W7.

---

### Post by cariboo on 2010-03-02
Seeing as the op has left, and doesn't want any help, there is no sense in keeping this thread open. Closed.

---

