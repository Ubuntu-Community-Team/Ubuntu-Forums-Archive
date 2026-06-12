---
title: "How to access cloud"
date: 2010-10-25
forum: Ubuntu Cloud and Juju
---

### Post by Chauhan Ankit on 2010-10-25
Hi guys,
I have just installed the 64 bit UEC , cloud controller and node controller.Actually i am implementing private cloud for my organisation, i opted for UEC . I have installed both cloud and node controller succesfully, downloaded an image of lucid lynx from store, i am using Hybrid Fox to manage the server.
Problems are-
-> When i try to run the instance of the image it says "No available Resources"
 Ya i used my own key pair for that.
Later when i tried to run it runs, i am unable to figure out what was the problem
-> How to access the cloud (by users on LAN ) or to make the best out of it. I searched quiet a bit but unable to find some document which can fully tells how to actually access the services in the cloud,after running their instances.:(

I am sure that there is much to do with the cloud. Plz solve the above two problems and also tell me some good resource to learn about the uec in detail. :)

---

### Post by kim0 on 2010-10-27
Hi!
I think you can resolve the problem by de-registering your cluster and then re-registering it and registering your node with it. Check out this thread for a similar situation and useful commands

[http://open.eucalyptus.com/forum/problem-node-registration](http://open.eucalyptus.com/forum/problem-node-registration)

---

