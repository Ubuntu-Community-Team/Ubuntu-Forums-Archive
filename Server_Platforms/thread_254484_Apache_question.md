---
title: "Apache question"
date: 2006-09-10
forum: Server Platforms
---

### Post by misterE0 on 2006-09-10
ok, i've got an apache server on my network.  The server functions as a file server as well as a xampp dev server.  Is there a way to a) set up something like  [URL="https://help.ubuntu.com/community/LocalhostSubdomain"]this/URL] so that it works across a local network? eg. if i make the server myserver.com and can access user.myserver.com locally?

---

### Post by misterE0 on 2006-09-13
anyone?

---

### Post by lamego on 2006-09-13
1. You need to setup an A or CNAME record on your intranet DNS server for your user.myserver.com.

2. You will need to setup user.myserver.com as a virtual host on your apache config as explained on the help page you have just posted.

---

