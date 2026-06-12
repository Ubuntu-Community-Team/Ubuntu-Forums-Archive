---
title: "Dansguardian config for a user account"
date: 2010-09-12
forum: Security
---

### Post by foxy123 on 2010-09-12
I have installed webcontentcontrol and I am trying to configure dansguardian for my daughter's account on my laptop. I just want it to filter webcontent only on her account not others. But it seems to block sites on all accounts. Also it blocks almost everything. It does not display the Ubuntu forum and blocks [http://www.gazeta.ru/](http://www.gazeta.ru/), which is a Russian news site for example saying that it is a porno site. Any help?

---

### Post by bodhi.zazen on 2010-09-12
I suggest you use iptables to direct or allow traffic.

See : [http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

for examples.

dansguardian will need to be customized a bit, there is no was the defaults will satisfy everyone.

Alternates would we opendns or, depending on your router, configuration router side.

---

### Post by wacky_sung on 2010-09-13
If you just configure for your daughter then you shall create an account for your laptop and let her login using the account you have created for her by pointing it to dansguardian.There may be other reasons why those sites are block can also be contributed if you are using browser addon or softwares.Beside that,i am not sure if dansguardian is able to filter out other languages other than English alone.So far,dansguardian work great for me testing with lot of sites with 99% percent accurate with default setting.

---

