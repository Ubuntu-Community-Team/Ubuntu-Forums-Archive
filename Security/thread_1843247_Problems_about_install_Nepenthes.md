---
title: "Problems about install Nepenthes"
date: 2011-09-13
forum: Security
---

### Post by johnnypham on 2011-09-13
hi everyone

I have a trouble of binding port when I run nepenthes :

> ERROR Could not init Socket Address already in use
[ crit net mgr ] ERROR Binding :5000 failed
[ spam net handler ] <in virtual nepenthes::TCPSocket::~TCPSocket()>
[ spam mgr event ] <in virtual uint32_t nepenthes::EventManager::handleEvent(nepenthes::Event*)>
[ spam net mgr ] bindTCPSocket 0 10000 0 30 1945870

I cannot fix it even though i used to reference in many websites. And log file is also not operate.

I need your helps as soon as possible.

I'm from Vietnam. Sorry about my language 

Johnny

---

### Post by Lars Noodén on 2011-09-13
"[Do not use Nepenthes, use Dionaea instead](http://nepenthes.carnivore.it/)."

Except that there is no package for Dionaea in the repositories.

Edit:  The request for Dionaea is now [bug #848975](https://bugs.launchpad.net/ubuntu/+source/nepenthes/+bug/848975).

---

