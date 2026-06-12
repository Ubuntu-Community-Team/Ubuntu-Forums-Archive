---
title: "GDM failed logins appear to generate internet connection activity: Why?"
date: 2009-03-09
forum: Security
---

### Post by krnlg on 2009-03-09
Hi guys,

If you've got a router with indicator lights for network and Internet connection activity, try typing some incorrect login details into GDM and watch what happens when the login fails and the prompt resets.

What I see is that the internet connection is used briefly. That is, the actual ADSL light, and not just the network light that flashes if I do ping <my_ip>.

Presumably I would be wrong in thinking that something is being sent outside my home network whenever an incorrect login attempt is made? In which case, what is happening here that I'm misunderstanding?
Failed logins from the console and with sudo do not have this effect.

So I figured you good people in the Security forum might know something about how GDM works that could be causing this, and maybe give me some reassurance that its not a security issue! :D

Thanks in advance!
Josh

---

### Post by cdenley on 2009-03-09
I just tried this, and nothing is sent by my computer using intrepid.

-install tcpdump and wireshark
```

sudo apt-get install tcpdump wireshark

```
-log out
-switch to terminal (ctrl+alt+f1)
-login to terminal
-start capturing network traffic
```

sudo tcpdump -i eth0 -w gdm.pcap

```
-switch back to GDM (ctrl+alt+f7)
-attempt login with a bad password
-switch back to terminal (ctrl+alt+f1)
-stop tcpdump (ctrl+c)
-switch back to gdm (ctrl+alt+f7)
-log in
-view captured network traffic
```

wireshark gdm.pcap

```

---

### Post by krnlg on 2009-03-10
Thanks for that! Seems to be nothing more than a couple ARP packets between the router and my NIC. No idea why it triggers the router's adsl status indicator though. Or why its necessary only for failed logins. But I guess its innocuous =D>

---

### Post by lavinog on 2009-03-10
Are you using hardy or intrepid?
I think in hardy it would do a dns resolution
This was an issue when using sudo and the hostname couldn't be resolved...maybe a similar thing is happening.

---

### Post by krnlg on 2009-03-13
[quote=lavinog]Are you using hardy or intrepid?
I think in hardy it would do a dns resolution
This was an issue when using sudo and the hostname couldn't be resolved...maybe a similar thing is happening.[/quote]

I'm using Intrepid. There are a couple DNS resolutions looking up localhost, if I'm reading what wireshark says correctly, so I think you might be right.

Anyway I guess its ok. It was just hard to see how a login failure could possibly be related to network activity :)

---

