---
title: "Developing on Open-Source"
date: 2014-04-29
forum: Ubuntu, Linux and OS Chat
---

### Post by matt.lawrence on 2014-04-29
I was told that if I were to develop software for Ubuntu or another Linux distro, or even use an open-source IDE that my software would have to be open-source as well. Is that true?

---

### Post by Elfy on 2014-04-29
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Why don't you go and look at licenses :)

---

### Post by sotiris2 on 2014-04-29
Unless you include open source code **in** your program you won't have to open-source you own code. There are even open source libraries with a different license to allow linking without having to open source your program.  

In regards to the IDE, would you believe that using Gimp to retouch your photo would make you lose your copyright? Or libre-writer to write a book would make you lose copyright? Or do you fear that the IDE will stealthily add a gpl to your code? Usually only open-source code 'accidentally' makes it to the program rather than an open-source license.

---

### Post by Lars Noodén on 2014-04-29
> **matt.lawrence said:**
> I was told that if...

Out of curiosity, where did you hear that?

---

### Post by SeijiSensei on 2014-04-29
It's a pretty common FUD remark about open-source in the proprietary world, particularly the GPL.  Microsoft launched an [anti-GPL campaign]("http://www.nytimes.com/2001/05/03/technology/03SOFT.html") around 2001, and I'm sure some of that attitude continues today.  Microsoft enjoyed the fruits of projects like Kerberos, because its license is so liberal.  The GPL was derided as a threat to American innovation.

OP, this is a complicated issue, but in general you do not need to open your code just because you use open-source tools.  However there are issues about linking to libraries; there's something called the "Lesser General Public License" to cover that circumstance.  Also, all "open-source" is not licensed the same way.  The GPL is a very restrictive license, but others like the "MIT license" that covers X and Kerberos or the [BSD]("http://www.freebsd.org/copyright/freebsd-license.html") license essentially give the code away with no strings attached other than including a copyright notice.

I suggest you start reading here: [http://opensource.org](http://opensource.org)

---

