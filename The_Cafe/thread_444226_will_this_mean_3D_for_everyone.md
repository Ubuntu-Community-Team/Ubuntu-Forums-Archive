---
title: "will this mean 3D for everyone?"
date: 2007-05-15
forum: The Cafe
---

### Post by mykalreborn on 2007-05-15
so ATI will release their drivers open-source. my question to you is: will this mean my Radeon 9200 (currently usupported by compiz and beryl) will work with these kind of apps?

---

### Post by frup on 2007-05-15
MY 9200SE works great with feisty's desktop effects.

---

### Post by Kalixa on 2007-05-15
> **mykalreborn said:**
> so ATI will release their drivers open-source. my question to you is: will this mean my Radeon 9200 (currently usupported by compiz and beryl) will work with these kind of apps?

I have fully working 3d effects on my ATI Radeon 9200. Feisty is although the first distro ever were it worked. And it was out of the box!

---

### Post by forrestcupp on 2007-05-15
Yeah, but you guys that got it working did it by using the current open-source drivers.  You aren't using the binary fglrx drivers from ATI.  If you use ATI's drivers, you have to use XGL to get Compiz/Beryl working.  If you use the current open source drivers, Compiz/Beryl works with AIGLX, but they don't support all of the opengl features.

I think eventually the community will get ATI's released open source drivers to work well with everything.  But who knows how long it will take?

---

### Post by macogw on 2007-05-15
> **mykalreborn said:**
> so ATI will release their drivers open-source. my question to you is: will this mean my Radeon 9200 (currently usupported by compiz and beryl) will work with these kind of apps?

That card is supported.  Use the open source radeon driver.  Everything up to Radeon 9250 (I think that's the last one) is supported by the current open source driver.

Forestcupp, why would you WANT to use XGL instead of AIGLX?  XGL is sllloooooowwwwwwww

---

### Post by mykalreborn on 2007-05-16
> **macogw said:**
> That card is supported.  Use the open source radeon driver.  Everything up to Radeon 9250 (I think that's the last one) is supported by the current open source driver.

Forestcupp, why would you WANT to use XGL instead of AIGLX?  XGL is sllloooooowwwwwwww

trust me. i've tried everything i could. it's unsupported.

---

### Post by forrestcupp on 2007-05-16
> **macogw said:**
> That card is supported.  Use the open source radeon driver.  Everything up to Radeon 9250 (I think that's the last one) is supported by the current open source driver.

Forestcupp, why would you WANT to use XGL instead of AIGLX?  XGL is sllloooooowwwwwwww

That's my point.  No one would want to use XGL.  With the current open source ATI drivers (that are not from ATI) you can use AIGLX which is a MUCH better method.  But with ATI's binary fglrx drivers AIGLX doesn't work so you have to use XGL.

But the problem with the current open source drivers is that they do not support all of the opengl features, which means a lot of opengl games and apps will not work.  If you use ATI's fglrx drivers, all of these features work.  So, for the moment, you have your choice between being able to use AIGLX or being able to run opengl apps/games.

The fact that ATI is making their fglrx drivers open source means that the community will eventually get them up to speed, and users will be able to do AIGLX and opengl.  But this will take time, and who knows when ATI will actually release their code.

Edit:
The interesting thing about using ATI's drivers with XGL is that XGL won't let you run opengl apps very well either.  For now, it's just a big mess no matter what you do.  But it's changing.

---

