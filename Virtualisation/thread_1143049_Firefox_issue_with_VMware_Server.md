---
title: "Firefox issue with VMware Server"
date: 2009-04-29
forum: Virtualisation
---

### Post by RebelsAreWe on 2009-04-29
Intrepid
Gnome

I downloaded and installed VMware 2.0.1 and have run through the configuration and everything seems like it went through ok, but when I try to run it I get

micah@micah:~$ vmware
Launching VMware Web Access using /usr/bin/xdg-open
Error showing url: Failed to execute child process "/home/micah/Desktop/firefox/firefox" (No such file or directory)


Any ideas? :confused:

---

### Post by veloce on 2009-04-29
> **RebelsAreWe said:**
> Intrepid
Gnome

I downloaded and installed VMware 2.0.1 and have run through the configuration and everything seems like it went through ok, but when I try to run it I get

micah@micah:~$ vmware
Launching VMware Web Access using /usr/bin/xdg-open
Error showing url: Failed to execute child process "/home/micah/Desktop/firefox/firefox" (No such file or directory)


Any ideas? :confused:

Do you have firefox installed?

Have you changed default locations for things?

In the meantime, load your browser manually and navigate to:

[https://localhost:8333/](https://localhost:8333/)

and see if you get a response (log in prompt).

---

### Post by RebelsAreWe on 2009-04-30
> **veloce said:**
> Do you have firefox installed?

Have you changed default locations for things?

In the meantime, load your browser manually and navigate to:

[https://localhost:8333/](https://localhost:8333/)

and see if you get a response (log in prompt).

Yes

No

localhost:8333 uses an invalid security certificate.

The certificate is not trusted because it is self signed.
The certificate is only valid for micah

(Error code: sec_error_ca_cert_invalid)

---

### Post by RebelsAreWe on 2009-04-30
I added an Exemption and got through the error, but now it's saying [COLOR=#B0000F][FONT=Verdana]You do not have permissions to login to the server.[/FONT][/COLOR]

---

### Post by RebelsAreWe on 2009-04-30
All issues resolved with running it. Now I've just got issues setting up a VM. Haha off to the VMWare forums I go.


Thanks!

---

### Post by veloce on 2009-04-30
> **RebelsAreWe said:**
> All issues resolved with running it. Now I've just got issues setting up a VM. Haha off to the VMWare forums I go.


Thanks!

Excellent.

Have fun with it!

---

