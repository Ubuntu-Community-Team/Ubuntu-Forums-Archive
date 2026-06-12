---
title: "Strange firefox / ssh behaviour"
date: 2009-04-25
forum: Security
---

### Post by Shootfast on 2009-04-25
Howdy folks,

My issue first popped up in the alpha, and the thread I raised went unreplied and is now closed but I have noticed some perculiarity when using firefox over ssh.

I have a small server running Hardy x86_64 and Vmware server. When I couldn't remember the address for the Virtual Infrastructure web access I figured I'd just shell in and run "vmware".
The expected behavior was that firefox would launch on my hardy server and it's X session would be forwarded to my own Jaunty x86_64 box (I can tell which is which by the GTK themes not matching). I have done this on intrepid many times.

On Jaunty, after I ssh -X into my hardy server and run "vmware" (which just starts firefox at the vmware address) The local copy of firefox suddenly got a new tab with the new page in it.
As cool as this was (the remote firefox mingling with my local firefox) This was not the intended behaviour, and indeed just having an X forwarded shell open means that If I launch firefox from anywhere on my local machine when it isn't already running, it starts from the remote box and forwards over! (The themes don't match and my homepage is different!)

Is this a new *feature*? I didn't want to file a bug report in case this was the expected result, but it's definitely not what it used to be!

Local: OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
Remote: OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007

Cheers.

---

### Post by pytheas22 on 2009-04-25
I've seen behavior like this on Intrepid.  It seems to happen if I try to forward Firefox via X11 over a slow connection.  After a minute or two of waiting, a new instance of Firefox (not a new tab, but a whole new window) will open up, but I can tell from the theme (and from trying to save a file) that Firefox is running on the local machine, not remotely.  I assume it has to do with the network connection not being fast enough (it seems like after waiting a while to open Firefox remotely, it times out and opens a local session instead or something...perhaps there's some setting that tells it to do this), but that's just a guess.

If I forward a different browser, like Epiphany, it works, which is interesting.  Can you try that to see what happens?  You should still be able to access your VMware web interface in Epiphany.

---

### Post by HermanAB on 2009-04-25
Yup, if you want to use FF remotely, then you have to close any running local copy first.

---

### Post by Shootfast on 2009-04-26
Both machines are on gigabit cards sitting less that 2 meters apart. I dont think its a slow connection :)

I can access the VMware page fine now without the forwarded X, I just find it odd that suddenly my ssh session is leaking out into my local machine.

Is there any documentation that points to this behaviour?
I was under the assumption that running an ssh shell tunnels all requests to the remote machine, and any X window requests get pushed through to my local display. There shouldn't be any interaction between windows from my local or remote boxes short of copy and paste managed by my X server.

---

### Post by bodhi.zazen on 2009-04-26
This feature is built into firefox (yes it is odd).

If you ssh -X and try to forward firefox, it starts on your local machine.

The solution, if you want to forward firefox, is to use the -- no-remote option.

```
firefox --no-remote
```

Firefox has acted this way as long as I can recall ;)

---

