---
title: "Ubuntu 12.10 Beta almost runs all functions on Virtualbox 12.04 version"
date: 2012-09-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by afz12 on 2012-09-23
I have been following Ubuntu 12.10 developments over its alpha versions and now at 12.10 beta. It's shaping up really well so I installed U 12.10 on an older i3 2-core notebook and tried Virtualbox downloaded for Ubuntu 12.04 64 bit with the extension pack. All went well - actually the beta version is a good ambassador to the final version later this year! I used the terminal script to add me to the vbox users group

sudo usermod -a -G vboxusers my_first_name

and this turned up OK in /etc in file called "group" as vboxusers:x:125:my_first_name on its last line entry. 

However, as with similar posts, an imported XP VM ran OK on shared folder access (as entered in Virtualbox and interestingly the SD 16 GB card slot also worked fine)  but had no Internet access, (in this example, the host was MInt, virtualizing XP). Perhaps USB worked or did not. Ubuntu 12.10 beta 1 seems to run well in other regards (although the screenlet for battery status thinks it's absent!) butVirtualbox for U12.04 is understandably only part-compatible so fare.
  
My question is one of curiosity - are their any suggestions I can test for getting Ubuntu 12.10 beta 1 as a host to work in with a version of Oracle' Virtualbox that hasn't as yet been released? I am curious as these endeavours into Linux are quite educational.

Any suggestions are welcome - I am happy to test them out and see what whirls.

---

### Post by Perfect Storm on 2012-09-23
Moved to development forum.

---

