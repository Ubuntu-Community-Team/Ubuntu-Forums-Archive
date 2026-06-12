---
title: "Looking for a specific kind of file server."
date: 2008-08-23
forum: Server Platforms
---

### Post by Neodragon90 on 2008-08-23
Im trying to make a file server on ubuntu that my friends and I can use but id like to have it do certain stuff that my current file server can do.

My current file server config is on a windows comp running HFS. (HTTP File Server [http://www.rejetto.com/hfs/?f=intro](http://www.rejetto.com/hfs/?f=intro) is the site for it) 

This file server allows me to access files through a web browser upload them and download them. Kinda like ftp through a browser plus uploading(at least as far as I'm aware).

My problems with it are: its not secure at all, I would also like to be able to make folders and to delete folders and stuff. (The only way to do this is currently is through a local samba share at my house) and hopefully keep it in a simple web browser maybe even HTTPS...

The only current way I know that to do most of this would be to set up an ftp server and use it with an ftp client... which doesn't quite work when i cant install stuff on certain computers that i would be using this on.

I'm hoping that maybe someone here knows of just what I'm looking for is there's any place to find it its in the Linux(ubuntu) community.

PS: A gui (lol) would be nice for setting it up but cmd line and some good instructions could also work

Thx for reading all this and any ideas you come up with.

---

### Post by windependence on 2008-08-23
Actually this is easy. You just need to set up a webserver and allow directory listings. Then you just have to click on the file and download it. To protect it, you use an .htaccess file that sets a user name and password. It's not perfect but better than what you have now.

-Tim

---

### Post by Neodragon90 on 2008-08-29
Sorry it took so so long for me to get back to you but thanks for the reply I'll definitely have to try that.

Edit: BTW your icon is awesome...

---

### Post by freebeer on 2008-08-29
You might also want to look into [WebDav]("http://en.wikipedia.org/wiki/WebDAV").  It might be overkill for what you want to do, but I thought you might like to at least know about it.

---

