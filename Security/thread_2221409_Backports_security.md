---
title: "Backports security"
date: 2014-05-02
forum: Security
---

### Post by sagsaw-sawant on 2014-05-02
Are backports safe, secure and stable on a enterprise setup?

Also, should the universe and multiverse repositories be enabled on enterprise kind of a setup?

or its best to use the standard repository?

also how about extras and partners archives/repository?

---

### Post by claracc on 2014-05-02
Please, see : [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports), as the link says, bakports repositories don't have security support guarantee, also they can produce certain instability when interacting with the rest of the system.

About extra or partner repositories, you can find useful information here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by sagsaw-sawant on 2014-05-02
Thank you !!! Which means, its best to be with the default release repositories for an enterprise setup.

---

### Post by claracc on 2014-05-02
You are very welcome.

Yes, I think universe and multiverse repositories contain software mantained by community or privative third part software or commercial or manufacturers that you can use with a certain guarantee. I have them ebabled in my sources software file, please see attached image.

On the contrary I have disabled backports and proposed (not published) repositories since I think they can produce problems in a stable system. See the other attached image.

---

