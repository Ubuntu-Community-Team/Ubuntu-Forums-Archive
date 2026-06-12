---
title: "Playing Music / Video on Server"
date: 2009-08-22
forum: Server Platforms
---

### Post by Matsuri on 2009-08-22
k, here is an odd question. I have an Ubuntu 9.04 server setup in my room. I'm intending to place videos and music on it for community (roommates) use. I have a pretty nice sound card and graphics card in the server as it was an old machine of mine. I want to be able to plug the server into the TV through S-video and the sound system by 1/4" headphone jack. What programs / settings / things do I need to do so the server will pipe video and audio to the TV / speaker setup?

Thanks,
Matsuri

EDIT: I guess what my question boils down to, is there a low-end media player for the Server edition? Just enough to play the movies / music and pipe them through s-video?

---

### Post by gobbledigook on 2009-09-17
i use xbmc to play to my TV, but it needs X so you need to install some sort of desktop first. i access my server over ssh so having a gui is not too big an issue for me. 

i installed a stripped down version of kde with fluxbox and then wine, for utorrent, but never worked out how to write a script to make it start with the server. but xbmc works well and has an intuitive interface you can navigate around easily.

dan

---

### Post by guitar_man on 2009-09-17
Try using mocp 

> 
sudo apt-get install moc

after installing run it...type
> mcop 

dont know bout the video

---

