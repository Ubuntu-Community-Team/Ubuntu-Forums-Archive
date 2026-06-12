---
title: "Setting up Server on Ubuntu server with no GUI"
date: 2019-12-02
forum: Server Platforms
---

### Post by pocklinjackr on 2019-12-02
Im new to Ubuntu server and i Installed LAMP and Vesta Control Panel but im having trouble pointing my domain to my Control Panel, or whatever my domain needs to point to in the name-servers. Like i said new to this and dont really know what im doing

---

### Post by SeijiSensei on 2019-12-03
Does the server have a public IP address, or is it behind a router?

Where are your domain name records hosted? If the computer has a public address, you need at least an "A" record that points its name to its address like:
```
www     IN     A    10.10.10.10
```

If you have a mail server, your domain needs one or more "MX" records as well, directing incoming mail for the domain to the mail server.

Beyond this is more complicated than I want to get into.  This article is a bit technical, but then DNS is a technical subject: [https://www.slashroot.in/what-dns-zone-file-complete-tutorial-zone-file-and-its-contents](https://www.slashroot.in/what-dns-zone-file-complete-tutorial-zone-file-and-its-contents)

---

