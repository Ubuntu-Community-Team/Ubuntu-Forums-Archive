---
title: "Default Samba configuration not accessible from Windows"
date: 2011-08-16
forum: Server Platforms
---

### Post by Aikon- on 2011-08-16
Hi all,

I have recently done a fresh install of Ubuntu 11.04 Server (64-bit). I selected Samba during installation, but a subsequent ```
# apt-get install 
``` installed some additional packages. I have been using my actual smb.conf file as well as the default smb.conf file that ships with Samba for testing; both show the same results.

When I restart nmbd and smbd and then try to browse the server from windows with e.g. ```
\\servername\
```, I get the error "Windows cannot access \\servername\. Check the spelling of the name [blah blah blah]." The same error results if I use the server's IP address instead of name.

Suggestions? I feel like this is the kind of thing that should work out of the box.. I had a previous Ubuntu install on this computer which had Samba running fine, but it has since been wiped. I don't recall having to jump through any particular hoops to get it working last time.

-Aikon

---

### Post by Brad55 on 2011-08-16
Check your firewall setting on the Samba computer, not the windows one.

---

### Post by Aikon- on 2011-08-16
> **Brad55 said:**
> Check your firewall setting on the Samba computer, not the windows one.

I have done no firewall configuration whatsoever. This is a fresh Ubuntu install, with only
```
# apt-get install samba
// edit smb.conf file
# restart nmbd
# restart smbd
```.

-Aikon

---

### Post by PierreRobiquet on 2011-08-16
Can you ping both machines from each other or access SSH for example?

---

### Post by Aikon- on 2011-08-16
Ping and SSH both work from the Windows machine to the Ubuntu server (which is actually headless, so all administration is done via SSH), by both name and IP address. I haven't tried pinging the Windows machine from the server (and can't at the moment, as I am at work).

-A

---

### Post by Aikon- on 2011-08-16
I "solved" my issue by downgrading the installation to 10.04.3; computer is now visible from Windows network with no problems.

---

### Post by PierreRobiquet on 2011-08-16
10.04 uses a lower version of Samba so it may be a newer bug, although since 11.04 -> 10.04 is quite a large change I wouldn't isolate that as the only cause.

---

### Post by Aikon- on 2011-08-16
> **ConcreteDonkey said:**
> 10.04 uses a lower version of Samba so it may be a newer bug, although since 11.04 -> 10.04 is quite a large change I wouldn't isolate that as the only cause.

Agreed; I followed this downgrade for two reasons -- one, I had it working on 10.04 before, and two, 10.04 is still an LTS. Unfortunately, this is one of those situations where I don't have the time to invest in finding the true cause behind the 11.04 failure, when 10.04 works well enough for me. Maybe there is a bug there, or it's just some strange default configuration settings, or something weird with the particular way I installed that VM.

Regardless, it's working now, and I don't intend to touch it for a while. Thanks your peoples' help =)

-A

---

