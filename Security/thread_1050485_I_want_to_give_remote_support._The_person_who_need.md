---
title: "I want to give remote support. The person who needs support start the link"
date: 2009-01-25
forum: Security
---

### Post by Awareness on 2009-01-25
This is what I want to accomplish:

I want to give remote support to my mom's laptop. No matter behind what router she may be. For that, I want her to start the communication just giving her my ip...

This is what ive done (ill make an script when is done):

My mom's:
x11vnc -usepw -dispaly :0
ssh -R 5900:locahost:5900 -l support -p 123 THIS.IS.MY.IP

My comp: (its running sshd on port 123)
xtightvncviewer localhost

This works flawlessly, but I have some security concerns...

For example, i dont want ssh to give you a promt when you log with the support user in my account... any idea how to do so?

Is there a better way to do the remote support?

---

### Post by HermanAB on 2009-01-25
Either of these work:
[http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)
[http://www.vncscan.com/vs/oneclickVNC.htm](http://www.vncscan.com/vs/oneclickVNC.htm)

Cheers,

Herman

---

### Post by The Cog on 2009-01-25
That's just what I was thinking of doing for my mum.

An alternative might be to use openvpn. That would set up full networking between the machines so you can connect to any port she has open. It's a tad harder to configure initially, but I think it would prove very robust and secure. Come to think if it, that's what I'll do for my mum. A bonus is that an openvpn server uses certificates so it's not vulnerable to password guessing.

---

### Post by HermanAB on 2009-01-25
The VPN will give you networking but it won't give you control.

---

### Post by krunge on 2009-01-25
> **Awareness said:**
> 
My mom's:
x11vnc -usepw -dispaly :0
ssh -R 5900:locahost:5900 -l support -p 123 THIS.IS.MY.IP

My comp: (its running sshd on port 123)
xtightvncviewer localhost

This works flawlessly, but I have some security concerns...

For example, i dont want ssh to give you a promt when you log with the support user in my account... any idea how to do so?


x11vnc has SSL support and you can use a reverse connection. On your side, ssvnc is a wrapper around tightvncviewer that provides SSL (or roll your own with stunnel or socat).  In ssvnc you can select Options ->  Reverse Connection, uncheck Verify All Certs, and then click on 'Listen'

Then mom does:

```

mom> x11vnc -ssl SAVE -connect_or_exit THIS.IS.MY.IP:5500

```

You have opened port 5500 as you did 123.

Optionally, ssvnc is also able to verify your mom's cert, and x11vnc is able to verify your ssvnc cert. Or the -usepw you have set up might be enough.

There are some more ideas here: [http://www.karlrunge.com/x11vnc/faq.html#faq-singleclick](http://www.karlrunge.com/x11vnc/faq.html#faq-singleclick)


If you want to stick with SSH and I understand your concern correctly, you might be able to use ssh-agent(1) and add the key before running ssh.  That will avoid the prompt.  Unfortunately you'd need the key to have no passphrase to avoid all prompts.  Probably not a good idea.  I don't think you explained your security concerns with your method completely; so I may have missed your point.

---

