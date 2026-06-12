---
title: "Can Foobar2000 use wineasio?"
date: 2008-12-28
forum: Wine
---

### Post by chaozh on 2008-12-28
I have AudioFire2 1394 sound card. I installed ffado and jack server and they can works well. I can play music or movie through mplayer with audiofire2. But I have many ape/flac music. So I want to use foobar2000 under wine and hope foobar2000 can play through audiofire2. From google. seems wineasio can do it. I installed it but foobar2000 still can not work on audiofire2. Anybody can help me or have a good idea? Thanks a lot!

---

### Post by LuisUK on 2011-09-04
Well, that depends on the version of Foobar's Asio output component.

Otachan's foo_output_asio works with wineasio, but it's for foobar 0.8.3. It will not work with any newer version of Foobar (unless you want to recompile it against a newer Foobar source, which I don't know if/how it can be done). The newer foo_out_asio does not work with wineasio (it gives an error - "No ASIO driver found").

So, it seems that if you want to use foobar with wineasio, you'll have to use 0.8.3 and Otachan's foo_output_asio.

Another way to get Foobar to play through Jack and Audiofire2 is to select Jack output in winecfg and Wine Jack DirectSound Driver in Foobar. This works for me with the latest version of Foobar, Wine 1.3.27 and Jack 1.9.7.

---

### Post by LuisUK on 2013-01-02
It appears that there is a way to make the latest foobar version (1.1.8) work with wineasio (using Wine 1.4.1). It involves installing ASIOProxy (foo_dsd_asio) and then setting it as output in foobar. In foo_dsd_asio's control panel, set asio driver to wineasio.

---

