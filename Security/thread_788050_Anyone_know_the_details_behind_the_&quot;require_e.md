---
title: "Anyone know the details behind the &quot;require encryption&quot; checkbox in Remote Desktop?"
date: 2008-05-09
forum: Security
---

### Post by antistar. on 2008-05-09
I'm trying to find out more details regarding encryption on the Remote Desktop server/client in Hardy. Anyone have any details as to what it does/doesn't encrypt, level of encryption, protocols used etc. ?

I'm hoping that it automatically enables and sets up an SSH tunnel but I can't find any docs to support that. 

Just want to make sure I have a reasonably secure connection to my Ubuntu PC back home. 

I'm aware of the VNC/SSH thread here but I don't want to reinvent the wheel if it's not necessary. 

Thanks!:)

---

### Post by timcredible on 2008-05-09
here's the [info]("http://technet2.microsoft.com/windowsserver/en/library/a92d8eb9-f53d-4e86-ac9b-29fd6146977b1033.mspx?mfr=true") on RDP encryption (RDP is the protocol windows uses for remote desktop).  imho, rdp and xdm are much better than vnc because they are native to their respective OS.

---

### Post by cdenley on 2008-05-09
I think he was referring to vino, which can be configured at...

System>Preferences>Remote Desktop

All you need to enable and setup a server which supports SSH tunneling is to install an ssh server. It is up to the client to establish the SSH connection with a port-forwarding option, then connect to the VNC server though the encrypted tunnel. I don't think the option you are referring to prevents vino from listening on external interfaces, but forces the clients to use TLS/SSL (if supported). This would be a simpler solution so you only have to authenticate once with a single client. I'm not sure how vino's encryption compares to ssh.

[http://www.gnome.org/~markmc/remote-desktop.html#encryption](http://www.gnome.org/~markmc/remote-desktop.html#encryption)

---

### Post by Darrena on 2008-05-09
It looks like it is TLS for the password:
[http://www.gnome.org/~markmc/remote-desktop.html](http://www.gnome.org/~markmc/remote-desktop.html)

However it looks like the RFB stream is still not encrypted and I don't know all the details on how the certificates were generated for TLS encryption.

So I would recommend that you just tell Vino to only accept local connections and tunnel your connection over SSH if security is important.

---

### Post by antistar. on 2008-05-14
Sounds good - better safe than sorry :)

---

