---
title: "Is this outbound connection something to worry about?"
date: 2010-02-16
forum: Security
---

### Post by markling on 2010-02-16
I had a request for an outbound connection on my computer. It was made in a warning dialogue.

It was described as potentially dodgy. I was told to click <settings> to allow the connection. I clicked on settings (its late, I'm tired, and I thought against my instincts that it would give me an option to set the settings and see what it was all about). The dialogue disappeared. The only other option it had given me was <OK>.

It was asking for a connection to the following site: admin.brightcove.com.

It said the name of the requesting application was called "object". I think it may have been Adode that had given the warning. It said the settings would be set on restart.

Brightcove seems to be some sort of video service. I was not using any video other than may have been appearing in web adverts. I have never been asked this message before.

Have I let a malicious thingymajib call out on my machine? Or is there a prefectly reasonable explanation?

---

### Post by adam814 on 2010-02-16
Well, I haven't seen that particular warning dialog myself.  Brightcove definitely serves up web ads alright.  With any luck the worst that will happen is a tracking cookie or two you can just remove.  NoScript (while not perfect) can be a lifesaver for those kind of things as well.

---

### Post by markling on 2010-03-07
thanks, adam. i'm sorry to be replying so late to your message.

i was using Chrome at the time this happened. but will shall have a try of Firefox's NoScript.

I mailed brightcove about it, but got no reply.

Like you say, one can only hope its just a tracking cookie. It does seem, however, that my system has been compromised. I shall see if about scanning for problems.

---

### Post by OpSecShellshock on 2010-03-07
Brightcove is a company that provides platforms for online media content delivery. I'm not sure why your computer would have been sending something out to it unless it was a request for content of some kind. It would depend on the site you were viewing at the time. It appears that some news organizations use it to deliver audio and video, and I'd imagine other types of sites do so as well. There was likely an object embedded in a page you were viewing, and since it was stored on a different domain than the rest of the content of the page, the browser prevented it by default and just gave you the option of retrieving it if you wanted to. That's a good thing.

Oh, it looks like companies that use the platform for ad content also run it from the admin server, so it could well have been that, too. Either way, whatever setting in the browser got changed can also be changed back. I don't use Chrome myself, so I wouldn't know where those settings are. I will say this, though: that particular browser was made from the ground up by a company that makes its money through advertising and tracking user behavior. They may not allow as much user control over that kind of thing as other browsers would.

---

### Post by Jive Turkey on 2010-03-07
I you're worried about it you could ad a line like this to your /etc/hosts file.  even if you had some software phoning home to brightcove.com it wouldn't get a connection.

```
0.0.0.0 brightcove.com
``` This might screw up your ability to view ads and other content hosted at brightcove but who really cares.

---

### Post by markling on 2010-03-08
Thanks chaps. The brightcove request was unusual in that I've never seen the like before or since.

The hosts file recommendation is a great tip, thank you.

For any other beginners who need hand-holding, you can find specific instructions for editing the hosts file here:

[http://ubuntuforums.org/showthread.php?t=168357](http://ubuntuforums.org/showthread.php?t=168357) 

Having looked into it, I have gone further and added this list of blocked hosts, which is recommended for helping prevent connections to malicious sites and trackers:
 
[http://www.mvps.org/winhelp2002/unwanted.htm](http://www.mvps.org/winhelp2002/unwanted.htm)

This Ubuntu HOWTO was helpful on this topic:

[http://ubuntuforums.org/showthread.php?t=241460&highlight=mvps](http://ubuntuforums.org/showthread.php?t=241460&highlight=mvps)

---

### Post by markling on 2010-03-08
Except that it doesn't seem to have worked.

I can still browse to [http://www.brightcove.com](http://www.brightcove.com) in either Chrome or Firefox.

Even though I added this line to my hosts file:

0.0.0.0 brightcove.com

(I restarted browser, I restarted computer - no effect).

---

### Post by markling on 2010-03-08
I got it to block connections to brightcove only after adding the following two lines to the hosts file:

0.0.0.0 [www.brightcove.com](www.brightcove.com)
0.0.0.0 admin.brightcove.com

(and restarting the machine).

I don't know what difference the www. should make?

---

### Post by adam814 on 2010-03-08
You might need to wildcard it, as in:

```
0.0.0.0     *.brightcove.com
```

---

### Post by markling on 2010-03-08
thanks.

---

