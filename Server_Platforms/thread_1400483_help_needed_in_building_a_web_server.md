---
title: "help needed in building a web server"
date: 2010-02-06
forum: Server Platforms
---

### Post by xmask on 2010-02-06
Hello all,

I'm using ubuntu Lamp server. The thing is that I want to develop a web site that would contain Arabic language text. What I want to ask is that how come php editor support the Arabic text? Should I use unicode in php to show Arabic text on my web site? What if I develop my website in GUI php editor and then move it to my ubuntu server? Please explain which is the preferable method. Thank you for your time.

bye

---

### Post by hessiess on 2010-02-07
> **xmask said:**
> Hello all,

I'm using ubuntu Lamp server. The thing is that I want to develop a web site that would contain Arabic language text. What I want to ask is that how come php editor support the Arabic text? Should I use unicode in php to show Arabic text on my web site? What if I develop my website in GUI php editor and then move it to my ubuntu server? Please explain which is the preferable method. Thank you for your time.

bye

Just make sure that PHP and mysql support unicode and that you specify the page encoding as utf8. Generally it should just work.

---

### Post by xmask on 2010-02-09
> **hessiess said:**
> Just make sure that PHP and mysql support unicode and that you specify the page encoding as utf8. Generally it should just work.

suppose 1552 is a unicode of an Arabic character then what would be the statement to display that character on my page if i'm writing my code in any php editor avaiable on ubuntu server. thanks

---

