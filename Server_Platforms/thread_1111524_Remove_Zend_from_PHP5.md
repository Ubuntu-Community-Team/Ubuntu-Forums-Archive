---
title: "Remove Zend from PHP5?"
date: 2009-03-30
forum: Server Platforms
---

### Post by chez17 on 2009-03-30
I installed the default LAMP stack from synaptics "mark by package" section. So I have the default installation for Intrepid. I am having seg fault issues with php5 and I think the Zend optimizer might be to blame. The problem is I can't seem to find where on the system this is, there is no zend module or and no zend folder. How would I go about removing zend from PHP5?

---

### Post by windependence on 2009-03-30
It's compiled in to PHP5. You need to install the non-zend package, but I doubt that is the problem.

-Tim

---

### Post by chez17 on 2009-03-30
I looked through synaptic and I couldn't find a php non-zend package. Could you be more specific? I know there is some other optimizer, Ion Cube I think, if installed that would it automatically uninstall zend?

---

