---
title: "WAN server file sharing access and streaming"
date: 2015-04-18
forum: Server Platforms
---

### Post by amerinde on 2015-04-18
hello all, i need more help. I think i have fried my brain. I need access to my server from the web, i can WOL and use webmin from any where, but how do i access the folders that are shared. I used to have a NAS, but it was too slow, so i set up ubuntu server to be faster.. I need folder access and streaming.

---

### Post by volkswagner on 2015-04-19
You should not open Webmin to the world (bad security practice).

There are some choices for sharing content via the web. Perhaps you can explain
more about the clients accessing the system.  Your NAS likely had a setup similar
to [eXtplorer]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCEQFjAA&url=http%3A%2F%2Fextplorer.sourceforge.net%2F&ei=PMYzVZStMbOasQTYo4HgAQ&usg=AFQjCNH6fSpEzb_chPewxDyZiALNb7_M5g&sig2=bUkmdj4T7S5cwxlKxGsGEg&bvm=bv.91071109,d.cWc"), [Owncloud]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&cad=rja&uact=8&ved=0CDgQFjAD&url=https%3A%2F%2Fowncloud.com%2F&ei=-MYzVafjNYrIsQSb4YGwDA&usg=AFQjCNF8j3oGRG9a2dFzUGknslvK8mqz0w&sig2=g4-BkKZ6E3iN0DBotBapgg&bvm=bv.91071109,d.cWc") may help here and perhaps streaming as well.

Streaming servers like Jinzora, Ampache or similar may be an avenue to explore.

---

### Post by amerinde on 2015-04-19
> **volkswagner said:**
> You should not open Webmin to the world (bad security practice).

There are some choices for sharing content via the web. Perhaps you can explain
more about the clients accessing the system.  Your NAS likely had a setup similar
to [eXtplorer]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCEQFjAA&url=http%3A%2F%2Fextplorer.sourceforge.net%2F&ei=PMYzVZStMbOasQTYo4HgAQ&usg=AFQjCNH6fSpEzb_chPewxDyZiALNb7_M5g&sig2=bUkmdj4T7S5cwxlKxGsGEg&bvm=bv.91071109,d.cWc"), [Owncloud]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=4&cad=rja&uact=8&ved=0CDgQFjAD&url=https%3A%2F%2Fowncloud.com%2F&ei=-MYzVafjNYrIsQSb4YGwDA&usg=AFQjCNF8j3oGRG9a2dFzUGknslvK8mqz0w&sig2=g4-BkKZ6E3iN0DBotBapgg&bvm=bv.91071109,d.cWc") may help here and perhaps streaming as well.

Streaming servers like Jinzora, Ampache or similar may be an avenue to explore.

The clients accessing it would be for streaming, mainly windows systems, but a few android and mac, Ampache looks like it would work for that. But, I would still need access to folders and files. I am not always in the room with the server, that's why Webmin is accessible.

---

### Post by volkswagner on 2015-04-19
Being in another room is different from "anywhere".  Please
specify if you want streaming from your own LAN or from other networks ie: over the Internet.

Having Webmin open to LAN is not what I was referring to. If you are opening/forwarding
Webmin port on your router for outside networks is bad.

---

### Post by TheFu on 2015-04-20
Use sftp for all file access from anywhere in the world - local or remote. It is secure, if you use ssh-keys for authentication. There are clients for every OS that is networked. If you need to allow other people to have access, set them up with chroot, non-shell, accounts to only the parts of the file system you want them to see. There are how-tos in many Linux server books.

I doubt you'd like my streaming solution - openvpn to lock down access and use any server you like - I use Plex Media Server. With openVPN, it is secure from anywhere in the world. There are clients for most OSes. Setting up openVPN is non-trivial, but it is required if you care at all about security and want to use owncloud, seafile and many webDAV file access tools.

Streaming audio is trivial and can work with gnump3 or 50 other tools.
Streaming video is harder and depends on the video resolution, audio codecs, video codecs, clients involved, viewing screens involved, CPU, RAM available and most importantly - the network bandwidth available from the server to each of the clients.

---

