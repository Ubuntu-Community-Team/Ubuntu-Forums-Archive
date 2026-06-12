---
title: "Problem:GModule-CRITICAL **: g_module_close: assertion `module-&gt;ref_count &gt; 0' failed"
date: 2013-04-02
forum: Ubuntu Application Development
---

### Post by sherwin2008 on 2013-04-02
After complied Skeltrack, a n error happened when running the example.: 


root@ubuntu:~/Skeltrack/examples# ./test-kinect 

(lt-test-kinect:2069): GModule-CRITICAL **: g_module_close: assertion `module->ref_count > 0' failed

(lt-test-kinect:2069): Clutter-CRITICAL **: Unable to initialize Clutter: Failed to connected to any renderer due to constraints
root@ubuntu:~/Skeltrack/examples# 
root@ubuntu:~/Skeltrack/examples# 

Any suggestions for this.

---

### Post by sherwin2008 on 2013-04-04
Any body can help?

---

### Post by sherwin2008 on 2013-04-11
Any body can tell me this error is related to which library&#65311;

---

### Post by schragge on 2013-04-12
To [GLib](http://en.wikipedia.org/wiki/GLib).

---

