---
title: "Sftp"
date: 2009-08-12
forum: Server Platforms
---

### Post by sprouty on 2009-08-12
Hi,

I'm trying to upload some files to a sftp server, and keep having problem when connection due to the promt with password. so far i have got this 

#!/usr/bin/expect
spawn sftp -b /home/user/sendfiles.txt username@ipaddress <<-EOF
expect "password:"
send "passwrod\n";
interact


but come back with this error message:Permission denied (publickey,gssapi-with-mic,password).

anyone got a quick fix or different method?

cheers,
sprouty

---

### Post by sprouty on 2009-08-13
anyone?

---

### Post by DaithiF on 2009-08-13
just a guess ... do you really need the newline after the password?

---

