---
title: "Preparing Apache2 for the Zend Framework"
date: 2006-08-28
forum: Server Platforms
---

### Post by ahlt on 2006-08-28
I am aware that this thread might include PHP issues, so please correct me if this is the wrong forum for this kind of question.

I've recently been reading about the [Zend Framework](http://framework.zend.com), and I now want to test it out.

So I've followed several tutorials ([1](http://framework.zend.com/manual/en/zend.controller.getting-started.html#zend.controller.getting-started.server-configuration), [2](http://hades.phparch.com/ceres/public/article/index.php/art::zend_framework::tutorial)),  for setting up the webserver for use with this framework. But I still ain't getting it right.

What seems to be the problem is that Apache ain't sending the index signal by default, even though I have enabled mod_rewrite. Because everytime I try to access my test suite, the Zend Framework function noRouteAction() is called, and redirects me to /. Which should only appears when there is no signal.

But the odd thing is that the noRouteAction() function also appears when accessing the index file directly: localhost/test/index.php


Hope someone understand and are able to help me out here :)

---

