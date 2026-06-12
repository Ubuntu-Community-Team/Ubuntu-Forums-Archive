---
title: "ubuntu server &amp; festival"
date: 2008-05-25
forum: Server Platforms
---

### Post by henux on 2008-05-25
Hi,

I have Ubuntu Server 8.04 and I'm trying to test the Festival speech synthesis framework on my computer. When I run festival from the shell and try "(SayText ...)" I got this error:

Linux: can't open /dev/dsp

So I suppose I need to install some packages. Can you instruct me what packages I need and what needs to be done in order to get audio working on my system?

Thanks.

-- henux

---

### Post by kso on 2008-12-05
bump - also seeing similar issues, installing these do not create "/dev/dsp"

alsa
alsa-base
alsa-oss
alsa-utils
apmd
esound
esound-clients
esound-common

---

