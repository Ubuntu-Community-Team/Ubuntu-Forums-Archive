---
title: "New user permissions"
date: 2009-02-13
forum: Server Platforms
---

### Post by ddo1 on 2009-02-13
I've inherited a production server that was managed by another admin and I need a little help. We're bringing in a contractor for a couple months, and he needs only access to a folder that's inside the apache2 document root. Now I thought this would be simple, but its giving me a little trouble because he can only have access to this folder, and nothing else. I can't add him to the group because he'll get access to everything else, and can't change him to the owner because other users need to access that folder, so therein lies the dilemma. I'm probably thinking too hard, but I can't come up with a secure way to lock the contractor down.

Should I just change ownership of that folder to the contractor, and add everyone else to the contractor's group? Ive tried to jail him, but it doesnt give him rw access to that folder. There's also ACL, and I will try that shortly if I don't find another way around it.

He'll also need to access php and mysql commands, but ill deal with that at another time. Thanks in advance, i'm sure its very simple, but my head is shot right now.

Best.

---

### Post by bodhi.zazen on 2009-02-13
Well, there is no way to restrict access to a single directory if you are going to allow shell access.

Options may include FTP (vsftp or proftp) or apparmor.

[http://www.friedcpu.net/?p=70](http://www.friedcpu.net/?p=70)

---

