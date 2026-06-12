---
title: "Thin Clients Lagging"
date: 2012-04-25
forum: Server Platforms
---

### Post by jwsicomputing on 2012-04-25
Hello,
Currently I have an Edubuntu computer which is set to dish IP addresses to thin clients (the computers just set to boot from LAN) then the Edubuntu screen comes up and all is well on the thin clients and i can log in fine.

On the server games like open arena etc.. work fine, but on the thin clients the games lag incredibly even flash games on the internet!!!!
I have tried direct connection (no switch) and other things, but just cant' find the answer to why it lags!!!

HELP PLEASE!!!

James Webb

---

### Post by CeltaWeb on 2012-06-05
Hi James,

Did you sort out the lag issue? and also did you set up the thin client network yourself if so can you recommend any tutorials on how best to tackle a thin client network.

Thanks

---

### Post by LHammonds on 2012-06-05
> **jwsicomputing said:**
> Hello,
On the server games like open arena etc.. work fine, but on the thin clients the games lag incredibly even flash games on the internet!!!!

Thin clients typically do not do well with anything that requires video-like communication such as games and video.  They tend to favor text-only or vector graphics because it requires much less bandwidth/cpu.  The flash video or game may indeed run just fine on the server's console but trying to see the same screen-refresh rate over a thin client connection will probably not work so well even with a very good connection.

FYI - I have no experience with Linux flavors of thin client software.  My experience comes from Windows remote desktop, Citrix Metaframe and Citrix Xen server.

LHammonds

---

