---
title: "apache userdirs"
date: 2006-03-24
forum: Server Platforms
---

### Post by peanut butter on 2006-03-24
i have my userdir set up but i cant get others to work. i am a sudo user.
i have chmoded 744 and everything but can't figure it out.
should i try running apache as root?:confused:

---

### Post by wsanders on 2006-03-24
Could you explain what you mean? Also, Apache that comes with Ubuntu is configured to not let you run it as root.(and in order to allow running apache as root, you have to recompile from source) It's a bad idea, anyway; it poses major security risks.

---

### Post by peanut butter on 2006-03-24
there are 2 users:
paulb
gregb
i can access paulb's public_html dir by going to httlp://localhost/~paulb
but when i go to httlp://localhost/~gregb it gives me a 403 error i have done chmod but it just  gives me a 403

---

### Post by wsanders on 2006-03-24
Try chmod to 755.

---

### Post by peanut butter on 2006-03-24
i still get a 403

---

