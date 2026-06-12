---
title: "Firewall issue if ufw is enabled"
date: 2011-12-11
forum: Security
---

### Post by lonewolf88 on 2011-12-11
Lubuntu 11.10, dual boot Win 7 Pro SP1 Toshiba laptop.

If ufw is enabled, I cannot access my isp.

```
~$ sudo ufw status
[sudo] password for jp: 
Status: active

```Nothing else is listed.

If is disable ufw, I can access the isp, no problems at all.

two questions - with ufw disabled, do I have any firewall at all; and should I be concerned about the ufw issue, and how to fix?

---

### Post by OpSecShellshock on 2011-12-11
What is the output of the following?

```
sudo ufw status verbose
```

---

### Post by lonewolf88 on 2011-12-11
> **OpSecShellshock said:**
> What is the output of the following?

```
sudo ufw status verbose
```

At present ufw is disabled, but by activating I get 

```
Status: active
Logging: on (low)
Default: allow (incoming), deny (outgoing)
New profiles: skip
```

---

### Post by OpSecShellshock on 2011-12-11
Ah, there it is then. Your settings are inverted from how it's usually set up for most folks. Basically it's prohibiting all outbound connections.

Try this:

```
sudo ufw reset
```

Then:

```
sudo ufw default deny
```

Then:

```
sudo ufw disable && sudo ufw enable
```

And see if that works.

---

### Post by lonewolf88 on 2011-12-11
> **OpSecShellshock said:**
> Ah, there it is then. Your settings are inverted from how it's usually set up for most folks. Basically it's prohibiting all outbound connections.

Try this:

```
sudo ufw reset
```Then:

```
sudo ufw default deny
```Then:

```
sudo ufw disable && sudo ufw enable
```And see if that works.

Doh!

More fool me!

I need to give up these late night sessions.  Must have fiddles with the settings! 

Thank you!

---

