---
title: "switch user no longer works"
date: 2013-04-19
forum: Ubuntu Studio
---

### Post by youWho on 2013-04-19
Hi all. The "switch user" function seems to be totally hosed; I have no idea why. Googling brings no useful results so far. I don't know how to go about fixing this, partly because I don't know what the command line equivalent would be.

Any help would be much appreciated.

2 days ago I removed approx:amd64 (5.3-1), then did apt-get autoremove which removed 

openbsd-inetd:amd64 (0.20091229-2ubuntu2).
Then I ran Software Updater, which did the following:
```
Upgrade: jackd2-firewire:amd64 (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu1, 1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2), 
nvidia-current:amd64 (304.51.really.304.43-0ubuntu1, 304.88-0ubuntu0.1), 
libgl1-mesa-dri:amd64 (9.0.2-0ubuntu0.1, 9.0.3-0ubuntu0.1), 
libgl1-mesa-glx:amd64 (9.0.2-0ubuntu0.1, 9.0.3-0ubuntu0.1), 
libjack-jackd2-0:amd64 (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu1, 1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2), 
libjack-jackd2-0:i386 (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu1, 1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2),
libglapi-mesa:amd64 (9.0.2-0ubuntu0.1, 9.0.3-0ubuntu0.1), jackd2:amd64 (1.9.8~dfsg.4+20120529git007cdc37-2ubuntu1, 1.9.8~dfsg.4+20120529git007cdc37-2ubuntu2), 
libcurl3:amd64 (7.27.0-1ubuntu1.1, 7.27.0-1ubuntu1.2), 
libcurl3-nss:amd64 (7.27.0-1ubuntu1.1, 7.27.0-1ubuntu1.2), l
ibxatracker1:amd64 (9.0.2-0ubuntu0.1, 9.0.3-0ubuntu0.1), curl:amd64 (7.27.0-1ubuntu1.1, 7.27.0-1ubuntu1.2), flashplugin-installer:amd64 (11.2.202.275ubuntu0.12.10.1, 11.2.202.280ubuntu0.12.10.1), 
libcurl3-gnutls:amd64 (7.27.0-1ubuntu1.1, 7.27.0-1ubuntu1.2), 
nvidia-settings:amd64 (304.51-0ubuntu2, 304.88-0ubuntu0.2)
```

Then last night I clicked on "switch user" in the panel and started a guest session, which worked fine. I logged out of that, switching to my regular user, which also worked as per normal. But today "switch user" just doesn't do anything.

I'm using ubuntu studio quantal, 64 bit. This is probably not ubuntu studio specific, it's just that that is I imagine very relevant (LightDM, xfce, etc) Thanks for any help.

---

### Post by matt_symes on 2013-04-19
Hi

Please use code tags. It makes text copied and pasted from the terminal much easier to read. Code tags are the **#** button above where you write your text.

Anyway, open a terminal and type

```
/usr/bin/dm-tool switch-to-greeter
```

```
/usr/bin/dm-tool switch-to-guest
```

```
/usr/bin/dm-tool switch-to-user <user_name>
```

Do they fail and if they do, do you get any error messages.

Kind regards

---

### Post by youWho on 2013-04-19
First, thanks for your post. Second, I have in the past tried to use code tags but didn't know how. Sorry. I'll use that from now on.

Re this:
Oddly, when I just started up the computer just now I tried again the GUI way to switch users, and it worked. I had tried restarting earlier, before I posted, and I also had tried a perhaps irrelevant but anyway obvious thiing to try of deleting and then re-adding the "Action Buttons" item form the panel. Neither had worked. But now it's working, as per normal, and I have no explanation.

I did try your command line versions, all 3 of them, and they worked and no error messages were returned.

So I guess I should change this to "[SOLVED]", or should I?? I mean, it's working, but I have no idea why, and so it may have limited help value to anybody else. But I guess I should change it because at the very least your command line variations can be tried, if ever anybody has the same problem and reads the thread. Thanks again!

---

### Post by matt_symes on 2013-04-19
Hi

I'm glad it's fixed. :D

Sounds like your PC just had a funny 5 minutes. That happens.

As for marking it as solved, i'll leave that up to you ;)

Kind regards

---

### Post by youWho on 2013-04-19
I figured I should mark it "solved" since others looking for similar help might benefit from your suggestions. Thanks again. Ciao.

---

### Post by youWho on 2013-04-20
I may have spoken too soon: again the GUI for "switch user" isn't working...

Trying all 3 of the above command line alternatives kindly recommended by matt_symes: in all 3 cases the result is that in the xfce terminal window the cursor moves to the next line, and that's all. No error messages, no switching of the user or any other effect. Basically it doesn't do anything. Damn.

Aany ideas, anybody??? (Many thanks in advance.)

---

### Post by matt_symes on 2013-04-20
Hi

Could you please post the output of

```
echo $XDG_SEAT_PATH
```

and

```
lightdm --version
```

After that please run this command in the terminal

```
/home/"$USER"/lightdm/lightdm-1.4.0/utils/gdmflexiserver
```

Does that take you to the greater ?

**EDIT:** Everything is CASE SENSITIVE so use capitals where i have and lower case where i have.

Kind regards

---

### Post by youWho on 2013-04-20
Hi, and thanks again.

```

echo $XDG_SEAT_PATH
/org/freedesktop/DisplayManager/Seat0


```
```

lightdm --version
lightdm 1.4.0

```
Then :     ```

/home/"$USER"/lightdm/lightdm-1.4.0/utils/gdmflexiserver

```
doesn't invoke the greeter, instead it returns:
```

bash: /home/<myusername>/lightdm/lightdm-1.4.0/utils/gdmflexiserver: No such file or directory

```
I should add though that this time when I restarted the computer the GUI "switch user" button in the panel was working. The above results are thus after it was working again.
I don't know if this might be significant, but firefox crashed just before it stopped working (I was trying trickle [this time; don't know about last time] to see if that might allow me to cause websites that stream video to do so at lower quality because I'm obliged to use a USB dongle for web access and some websites just assume one has high bandwidth; that didn't work [I didn't really expect it would, but thought it was worth a try] and firefox crashed).

---

### Post by matt_symes on 2013-04-20
Hi

> bash: /home/<myusername>/lightdm/lightdm-1.4.0/utils/gdmflexiserver: No such file or directory

Actually that makes sense. I downloaded the source for lightdm a while ago. Its in my home directory. I thought the directory was a hidden one.

Does this file exist ?

```
/usr/lib/lightdm/lightdm/gdmflexiserver
```

Can you run this command (copy and paste it)

```

dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.DisplayManager $XDG_SEAT_PATH org.freedesktop.DisplayManager.Seat.SwitchToGreeter
```

Does that take you to the greater ?

Kind regards

---

### Post by youWho on 2013-04-21
Hi and thanks again.

That file does exist:
```
/usr/lib/lightdm/lightdm/gdmflexiserver
```

and running the command:
```
dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.DisplayManager $XDG_SEAT_PATH org.freedesktop.DisplayManager.Seat.SwitchToGreeter
```

does indeed take me to the greeter (that is it takes me to the choice of users to log in as, which I assume is what you mean).
But then I tried it the GUI way just after trying that and it too is at the moment working, which is I guess good---but it's hard to fix something that's only occasionally not working ;-)

(Editiing this) I forgot to post the result that was printed in the terminal:
```
 method return sender=:1.11 -> dest=:1.63 reply_serial=2
```

---

### Post by matt_symes on 2013-04-21
Hi

What you now need to do is run all those commands i have given you when you cannot change user.

They should help identify where the problem is (or at least where it is not).

Post back all the results including any error messages and anything displayed in the terminal.

Kind regards

---

### Post by youWho on 2013-04-21
Thanks really a lot. I'll do that. Don't know when this'll happen, but if/when it does I'll post the results.

By the way your Japanese proverb quote is excellent. Ciao

---

### Post by youWho on 2013-05-10
Hello Matt, I wonder if you're there. If so and you don't mind continuing with this thread (if you don't have time then no worries; thanks in any case). Just now "switch user" again wasn't working so I tried all of your suggestions:

When I try the following, in every case there's no effect. I tried "switch-to-user" with a different user from the one that was logged in, and out of curiosity, entering the name of the logged in user.

```
$ dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.DisplayManager $XDG_SEAT_PATH org.freedesktop.DisplayManager.Seat.SwitchToGreeter

$ /usr/bin/dm-tool switch-to-greeter

$ /usr/bin/dm-tool switch-to-guest

$ /usr/bin/dm-tool switch-to-user
```

```
 $ lightdm --version
lightdm 1.4.0
```

```
 $ echo $XDG_SEAT_PATH
/org/freedesktop/DisplayManager/Seat0
```

and

```
$ ls -l /usr/lib/lightdm/lightdm/gdmflexiserver
-rwxr-xr-x 1 root root 612 Oct  9  2012 /usr/lib/lightdm/lightdm/gdmflexiserver
```

I wonder, do you have any further thoughts?? Thanks in advance.

{edit] A short update: I just now tried shutting down and then booting again. I'm quite sure I've tried that before, but what I don't recall is whether or not I tried using the GUI "switch user" feature *before* plugging in the USB dongle I have that is a broadband modem dongle. This time I did try it first, and "switch user" worked. hmm. And trying it now with the dongle plugged in... still working. I wonder if that's related?

---

### Post by matt_symes on 2013-05-10
Hi

Did the dbus-send (or other) commands return any errors on the terminal, such as a time out ?

It's any output i was hoping to see and not the fact you had entered the commands as i did not really expect them to work.

Kind regards

---

### Post by youWho on 2013-05-13
Hi Matt
First, sorry for the delay before I answered!! Just due to circumstances.
Unfortunately I didn't think of letting the commands time out, though I did let them sit there for several seconds before cancelling with command-c. But I can say that other than the possibility that they might have returned some kind of message when they timed out, there was no feedback. That is, in each case the cursor mearly went to the next line and then nada.
(un)fortunately ;-) it's not possible to run the commands again to see what might happen when they time out because as I mentioned above the switch user functionality is again working. Good news for me, but bad news for the slow process of debugging (and then maybe helping others to deal with possible problems). It does seem to happen occasionally that user switching stops working tho, and the symptoms seem to be the same; next time it does I'll run the above commands again and let them time out, then I'llpost again.
Thanks again!
Best,
Sam

---

### Post by youWho on 2013-05-23
Hi Matt again (if you're there),

"switch user" is again not working so I'm trying the tests you recommended, this time allowing each to time out in case the messages are useful.

```

$ dbus-send --system --type=method_call --print-reply --dest=org.freedesktop.DisplayManager $XDG_SEAT_PATH org.freedesktop.DisplayManager.Seat.SwitchToGreeter

Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
```

/usr/bin/dm-tool switch-to-greeter
/usr/bin/dm-tool switch-to-guest
/usr/bin/dm-tool switch-to-user

```
all after timing out simply return
```
Unable to switch to <thing>: Timeout was reached
```
It's difficult to keep track of what I've done prior to "switch user" having problems since I only realize it's not working after quite a bit of computer use usually.
From now on I'll try testing it shortly after booting in case that turns out to reveal anything.

Thanks again.

sam

---

