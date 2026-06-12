---
title: "Ubuntu Cloud Computing"
date: 2009-06-15
forum: Virtualisation
---

### Post by hoboy on 2009-06-15
I have spend 3 days now to make getting start work without any success.

I have tried to follow this
[http://doc.ubuntu.com/ubuntu/serverguide/C/eucalyptus.html](http://doc.ubuntu.com/ubuntu/serverguide/C/eucalyptus.html)
1: I have the desk-top version of ubuntu 9.04
2:I haven't been able to make Eucalyptus with KVM. work.
3.I have Sun Virtalbox  runing on the my ubuntu 9.04 host.
can I use this that server 9.04 in the virtualBox ?
4. To accomplished the getting start do I have to have 2 different machine ?

---

### Post by HermanAB on 2009-06-15
VMware and Virtualbox are more general purpose and can run on almost anything.  If you have only one machine, then it is better to run VMware or Virtualbox.

To use KVM, you need hardware that supports it.  To make a 'cloud', you need multiple machines otherwise there is not much point to the exercise.  The machines should also preferably all be the same, else you are bound to have many hassles.

---

