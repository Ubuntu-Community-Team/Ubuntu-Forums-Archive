---
title: "UFW (Uncomplicated Firewall) blocking the viewing of windows network"
date: 2011-01-24
forum: Security
---

### Post by ptyo on 2011-01-24
Does anybody know a fix for UFW where I can allow the application gvfsd-smb-browse on incoming connections? I have allowed samba connections through the firewall but it is blocking windows networks. Wireshark shows almost random UDP ports being used when you double click on Network Servers / windows network?

---

### Post by mikewhatever on 2011-01-25
You could allow the local IPs or just the local IPs of individual computers (see the advanced tab). 
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by ptyo on 2011-01-25
Hmm.. Well I added the IP's of our DNS boxes and it worked fine. Thanks.:popcorn:

---

