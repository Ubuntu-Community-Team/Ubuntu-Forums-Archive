---
title: "what is 0.strikes.net.nz doing in my /etc/hosts"
date: 2012-01-14
forum: Security
---

### Post by vfclists on 2012-01-14
I just installed the latest Ubuntu Hardy server edition and when the installation, and on checking the /etc/hosts file, I see the the host name has 0strikes.net.nz appended to it.

I got this directly from a server providers disk. Is there some kind of joke or did the file come from a tainted mirror?

---

### Post by OpSecShellshock on 2012-01-14
Was it obtained by way of a link from the actual web page of the distribution? Are you geographically in or near New Zealand (don't have to answer that publicly, just consider it)? Is the server it was downloaded from in or near New Zealand? I think I read somewhere that NZ has implemented one of those ridiculous "three strikes" policies for infringing activities, maybe it has something to do with that? Not sure why an official iso would have a custom hosts file even if it did have something to do with that though.

Edit: I just noticed you mention Hardy, which I believe was 8.04. It was a long term support release, which generally means three years. That time has passed, so it's no longer being updated. It is probably worth looking into moving to 10.04 or later.

---

### Post by cariboo on 2012-01-14
> **vfclists said:**
> I just installed the latest Ubuntu Hardy server edition and when the installation, and on checking the /etc/hosts file, I see the the host name has 0strikes.net.nz appended to it.

I got this directly from a server providers disk. Is there some kind of joke or did the file come from a tainted mirror?


As OpSecShellshock said. Hardy is almost 4 years old, and no longer supported. It could be that whoever provided the disk, may have customized it, especially if it didn't come from Canonical/Ubuntu.

The current LTS (long term support) version is 10.04, which will be supported until April 2013, or you can wait until 12.04 is released in April of this year, and enjoy 5 years of support.

---

### Post by gr3g0s on 2013-03-18
I know this ia a WAY OLD topic :P
0strikes.net.nz is a NZ based VPN service and i've got absolutely no idea how its in the Hardy distribution (4years old) when 0strikes is less than 2 years old now.
do you still have a record of what IP it was tied to?
Cheers

---

### Post by oldos2er on 2013-03-18
Old thread closed.

---

