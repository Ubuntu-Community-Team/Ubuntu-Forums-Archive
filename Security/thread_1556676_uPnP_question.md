---
title: "uPnP question"
date: 2010-08-19
forum: Security
---

### Post by blazemore on 2010-08-19
If uPnP allows an application to request a port to be opened on a temporary basis, doesn't that completely defeat the point of a firewall?
What's to stop some malware developer simply requesting a port to be opened?

---

### Post by uRock on 2010-08-19
> **blazemore said:**
> If uPnP allows an application to request a port to be opened on a temporary basis, doesn't that completely defeat the point of a firewall?
What's to stop some malware developer simply requesting a port to be opened?
They already do use it as an attack method. UPnP is disabled on my router and I would recommend others do it. It is not a needed service.

---

### Post by blazemore on 2010-08-19
Isn't that incredibly stupidly fundamental?
Why have a firewall if it doesn't do anything?

It's like having a security guard who just lets everyone through if they ask.

---

### Post by uRock on 2010-08-19
I am not sure turning it off even has any effect on Linux, though I have read that disabling it will mess up some services, such as torrenting. I haven't tried Netflix on my Wii since disabling UPnP to see if it affects it.

---

### Post by OpSecShellshock on 2010-08-19
> **uRock said:**
> I am not sure turning it off even has any effect on Linux, though I have read that disabling it will mess up some services, such as torrenting. I haven't tried Netflix on my Wii since disabling UPnP to see if it affects it.

I have it disabled and Netflix on Wii works fine.

---

### Post by uRock on 2010-08-19
> **OpSecShellshock said:**
> I have it disabled and Netflix on Wii works fine.
Sweet!:D

---

### Post by movieman on 2010-08-19
> **blazemore said:**
> Isn't that incredibly stupidly fundamental?
Why have a firewall if it doesn't do anything?

The goal of uPnP is to allow anything to talk to anything without any user configuration.

Which is obviously an incredibly stupid idea outside of very strictly controlled networks. Unfortunately it looks good in sales brochures.

---

### Post by Agent ME on 2010-08-19
A virus can just open a connection to a remote server instead of trying to wait for a connection from a remote server. Disabling upnp just hampers some legitimate programs.

---

### Post by uRock on 2010-08-20
> **Agent ME said:**
> A virus can just open a connection to a remote server instead of trying to wait for a connection from a remote server. Disabling upnp just hampers some legitimate programs.
Virus on Linux? I haven't found any applications yet that are being hampered by the disabling of UPnP, though I am sure there are a few.

---

### Post by FuturePilot on 2010-08-20
> **uRock said:**
> Virus on Linux? I haven't found any applications yet that are being hampered by the disabling of UPnP, though I am sure there are a few.

Bittorrent. I know Skype uses it as well.

---

### Post by uRock on 2010-08-20
I am using Transmission without any problems(Downloading 10.04.1). Isn't there a way to configure the ports manually to make the applications work without UPnP, being that it was designed to make it easier, there should still be a not so easy way to set things up.

---

### Post by FuturePilot on 2010-08-20
> **uRock said:**
> I am using Transmission without any problems(Downloading 10.04.1). Isn't there a way to configure the ports manually to make the applications work without UPnP, being that it was designed to make it easier, there should still be a not so easy way to set things up.

Yes, disable UPnP in the preferences (random port selection should be disabled by default) and manually forward the port. However if you use DHCP your IP address is eventually going to change, breaking your forward.

---

### Post by uRock on 2010-08-20
> **FuturePilot said:**
> Yes, disable UPnP in the preferences (random port selection should be disabled by default) and manually forward the port. However if you use DHCP your IP address is eventually going to change, breaking your forward.
Cool, I have DHCP, but Cisco has DHCP reservations for all of my machines.

---

### Post by OpSecShellshock on 2010-08-20
(Skype also works fine for me without UPnP and without ports forwarded)

---

