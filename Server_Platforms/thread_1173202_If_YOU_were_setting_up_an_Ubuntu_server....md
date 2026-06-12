---
title: "If YOU were setting up an Ubuntu server..."
date: 2009-05-29
forum: Server Platforms
---

### Post by Roasted on 2009-05-29
What would you use? I'm talking in terms of Ubuntu Server versus the Desktop edition.

I've been around Ubuntu for a long time and swear by it, however I've never messed with the server edition in particular. I've used my desktop "as" a file server but that's as crazy as I've gotten.

We're implementing an Ubuntu Server at work (school district - 7 schools total, some spaced up to 8 miles apart) which will be housed in the high school. It is supposed to be a Library database management server. So all schools will "tie" into this server based on the web based GUI frontend that this open source library catalogging software offers.

Now that it's been ironed out in the "test" LAN, the decision has been made to push it out to the main network for the beginning of next year.

Now that you know the situation here, what do you recommend? Does Ubuntu Server offer certain features that the Desktop edition does not have? Can you run Ubuntu Desktop Edition as a Server without any issues? Are the differences merely less overhead and resource consumption with the Server Edition or is there something more I'm not aware of?

---

### Post by grantemsley on 2009-05-29
The differences mostly amount to what software is installed by default and what the kernel is optimized for.

The server version has a lot fewer things running at startup, so leave more resources free for other things.  It has a kernel that is compiled with different options to make it faster in the average server environment.

But, you can turn the server version into a usable desktop just by adding the ubuntu-desktop package.  Or you can install desktop and shutdown all the other stuff you don't need by hand.

---

### Post by Roasted on 2009-05-29
If you add the desktop to the server edition, does that automatically activate all of the additional services at startup? Or does it simply add the GUI and that's it?

---

### Post by netJackDaw on 2009-05-29
If you are planning to use a server in a production environment, you should consider using a version that is supported over a longer time. The LTS versions of Ubuntu server are supported for five years. No desktop Ubuntu is supported for that long.

If you install desktop environment on a server, those desktop components only get supported for the shorter time period thus leaving your server vulnerable to possible exploits.

Do not install desktop components on a server unless you know what this means in terms of security.

---

### Post by Iowan on 2009-05-29
> **Roasted said:**
> What would you use? I'm talking in terms of Ubuntu Server versus the Desktop edition.My server(s) are not the latest/greatest, so I'd install the latest LTS (currently 8.04) server-version.  My server won't need a word processor or games or graphics. If I really, really need a GUI, I'll probably try ebox.

---

### Post by cariboo on 2009-05-30
I would also agree, there is no need for a desktop. I would suggest you have a look at [Webmin]("http:///www.webmin.com/").

---

