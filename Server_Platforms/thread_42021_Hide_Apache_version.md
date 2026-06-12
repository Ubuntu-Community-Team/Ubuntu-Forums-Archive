---
title: "Hide Apache version"
date: 2005-06-15
forum: Server Platforms
---

### Post by loon on 2005-06-15
How to hide apache version and Ubuntu info when going to directory listing links?

---

### Post by Beernut on 2005-06-15
You can try ServerTokens I have not tried it but it seems to be what you are looking for.

[http://httpd.apache.org/docs-2.0/mod/core.html#servertokens](http://httpd.apache.org/docs-2.0/mod/core.html#servertokens)

---

### Post by LordHunter317 on 2005-06-16
Why do you want to do this?

If it's for security, it's pointless.

---

### Post by briansvgs on 2007-12-02
Why would removing the server information from a directory listings be pointless? I know that ubuntu and other linux systems in general are pretty secure, and you can still get this information through programs like nmap and stuff, but having less information about your system viewable makes the system more doesn't it?

---

### Post by MJN on 2007-12-02
No, it makes *you* think you're more secure yet you're not. It used to be a worthwhile security but time moves on as do the risks.

Assume the bad guys know everything (bar your passwords if you use them) - take that as the starting point and base your security with that assumption and you won't go far wrong.

Mathew

---

