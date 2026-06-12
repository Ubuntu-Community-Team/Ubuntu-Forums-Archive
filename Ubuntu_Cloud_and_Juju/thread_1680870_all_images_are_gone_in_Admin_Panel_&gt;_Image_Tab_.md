---
title: "all images are gone in Admin Panel &gt; Image Tab after image disable"
date: 2011-02-03
forum: Ubuntu Cloud and Juju
---

### Post by AndF0 on 2011-02-03
Hi guys,

I have the following problem:  
- I setup my cloud without problems.. 
- downloaded images via the "Admin-panel > Store" 
- the images showed up under the "Admin-Panel > Image-Tab"
- I disabled all images...   
  Now all images are gone under the "Admin-Panel > Image-Tab" 
  **How do I get back the images?   **
  I cannot re-download the images since it says "installed" in the      "Admin-panel > Store"


Help is appreciated  

Andy

---

### Post by raymdt on 2011-02-04
Hey,
how did you disable the images? Did you delete deregister or what?
Try this and tell if it helps (But only if your system is a testsystem )

> 
apt-get remove --purge image-store-proxy
apt-get install image-store-proxy


Remove the browser cache after reinstalling.
Regards

---

### Post by AndF0 on 2011-02-10
> **raymdt said:**
> Hey,
how did you disable the images? Did you delete deregister or what?
Try this and tell if it helps (But only if your system is a testsystem )



Remove the browser cache after reinstalling.
Regards


Hey, 
all I did was press the disable button in the Web-Admin-Panel (under images) of the cloud

i tried as you suggested.
Unfortunatly i didn't help. 
When running the command it says that there is no such package.

Any other ideas?

---

### Post by raymdt on 2011-02-10
Hi andF0,
sorry my fault.

```

apt-get remove --purge python-image-store-proxy
apt-get install python-image-store-proxy

```

---

### Post by AndF0 on 2011-02-10
> **raymdt said:**
> Hi andF0,
sorry my fault.

```

apt-get remove --purge python-image-store-proxy
apt-get install python-image-store-proxy

```


Yeah THX
that solved the problem.
I still don't understand why I have to go through this process. 
Is this a bug in UEC?

---

### Post by raymdt on 2011-02-10
Nice to hear that it works.
It is a bug in the image-store-proxy plugin.
Regards

---

### Post by vgokulakrishnan on 2011-03-04
I ve slightly different problem,
My Server1(cc), server2(node) and client server r under http-proxy
When I click Store tab in webUI, i get 
" ERROR 35: gnutls_handshake() failed: A TLS packet with unexpected length was received."
I tried purging and reinstalling python-image-store-proxy too, But didn't help.. :(
Any 1 has a solution, please say me asap..

And, I haven't uploaded any images of myown, doesn't it matter..

---

