---
title: "ubuntu server + owncloud server setup help"
date: 2014-03-24
forum: Server Platforms
---

### Post by Bailey_Allen on 2014-03-24
[COLOR=#000000]hey guys,[/COLOR]
[COLOR=#000000]i want to run a laptop 24/7 running ubuntu server + owncloud server...[/COLOR]

[COLOR=#000000]the aim here is to be able to access all my files on many machines from my LAN and via the internet.[/COLOR]

[COLOR=#000000]also after this is done i was hoping i could have multiple users, that could login and only be able to see folders they have access to...[/COLOR]
[COLOR=#000000]eg if they can read/write in their personal folder, read from a shared folder, and neither on someone else's personal folder, they should only see their own personal folder + the shared folder.

[/COLOR][COLOR=#000000]i have used freenas on a virtual machine and that was running nicely in my LAN, but users could see folders they aren't meant to be able to see.[/COLOR]
[COLOR=#000000]the reason this is important is because several family members dont get along and there will be family, friends and maybe friends parents all using this...[/COLOR]

[COLOR=#000000]i dont want 'jane lowe's folder' being seen by michael for example. (i understand he cant see whats inside but its better if they didnt know the folder existed)[/COLOR]

---

### Post by TheFu on 2014-03-25
FreeNAS can be setup with user/group permissions.  Each user can have their own HOME shared, only for that user. Of course, it depends on the clients which file sharing can/should be used.  Different shared folders can have different permissions.

Last fall, I setup owncloud for a trial, but ended up removing it. Too many things weren't working for me. Plus, since it is PHP, security is a real concern. The only solution for that appears to be running a VPN like openvpn.  All of this makes client access more secure, but slightly more complicated for an average end-user. 

Of course, if security isn't a concern, dropping owncloud on the internet **can** be done.

---

### Post by thufirhawat2 on 2014-03-25
I love owncloud. I would not save any secure data on it, but for sharing pictures, video clips, etc. with family and friends, it is darn near perfect. 

The user permissions are very simple, but should for the most part accommodate what you are trying to do. The users should not be able to "see" each other's folders, but if they click a file or directory to share, and select the option to share with another user, as they type the name of the user they would like to share with, owncloud will list users with matching credentials as they type in the dropdown. So if I want to share something with Karen, I would type Ka in the user field, and it would show Karen's username, but it would also show Katherine as a potential user to share with. 

They can't see anything that user has not shared with them, but they now know there is a Katherine user. If that is a problem, then maybe you could give everyone non-name related usernames. E.g. maybe Katherine could be "batgirl" if she is a comic book lover or something.

If you want to install owncloud, a couple of things I ran into that I will share for your benefit:

 1: Do not just do a standard sudo apt-get install owncloud from the default repositories, you will get an old version, go to the [owncloud documentation site]("http://doc.owncloud.org/") and follow the instructions to add their repository to your list and install it from there.

2: If you are going to have multiple users, use MySQL, not SQLite.

3: If you are on a 32 bit OS, you will be limited to a 1.5GB aggregate upload at a time. This is apparently an issue with PHP on 32 bit OSs.

4: It is recommended to run owncloud using SSL, so if you do not want to pay for a genuine CA, you will have to self sign your own certificate, but your users will get certificate errors unless you send them a copy of your certificate to install in their browsers. This initially scared some of my non-computer-savvy relatives, but they should be able to dismiss the certificate error and continue to the site.

Good luck, and have fun!

---

