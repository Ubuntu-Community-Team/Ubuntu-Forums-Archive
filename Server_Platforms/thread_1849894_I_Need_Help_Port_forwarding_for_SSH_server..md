---
title: "I Need Help Port forwarding for SSH server."
date: 2011-09-25
forum: Server Platforms
---

### Post by DJKEMMET on 2011-09-25
PREFACE: I don't care too much about speed. its a hobbyist server, I'm using it to learn

So I installed Ubuntu 11.04 on to my IBM Z61t laptop. it's connected to my home LAN wirelessly and works well so far.

WHAT I'VE DONE SO FAR:


$ sudo apt-get install openssh-server

it's successfully installed. 

$ ifconfig

used the IP address from wlan0 and port 22 

now I need help port forwarding! i need to know how to configure my router to allow me access from anywhere using my(what i know as) global IP.

I have a newer actiontec router from verizon and know how to login to it and get to the port forwarding section, I just need to know how to configure it!

any help would be greatly appreciated!

DJ!

---

### Post by Dangertux on 2011-09-25
The port forwarded would be 22 TCP to the IP address of the laptop on the LAN.

This should be helpful. [http://www.actiontec.com/howto/h2_detail.php?cat_id=3&id=9](http://www.actiontec.com/howto/h2_detail.php?cat_id=3&id=9)

---

### Post by DJKEMMET on 2011-09-25
> **Dangertux said:**
> The port forwarded would be 22 TCP to the IP address of the laptop on the LAN.

This should be helpful. [http://www.actiontec.com/howto/h2_detail.php?cat_id=3&id=9](http://www.actiontec.com/howto/h2_detail.php?cat_id=3&id=9)

thanks! so sofar I've done the following:
step 1
[step 1]("http://www.flickr.com/photos/djkemmet/6182110422/")
step 2
[ step 2]("http://www.flickr.com/photos/djkemmet/6181587089/")

does that seem about right?

---

### Post by DJKEMMET on 2011-09-25
> **DJKEMMET said:**
> thanks! so sofar I've done the following:
step 1
[step 1]("http://www.flickr.com/photos/djkemmet/6182110422/")
step 2
[ step 2]("http://www.flickr.com/photos/djkemmet/6181587089/")

does that seem about right?

come on forums don't fail me now!

---

### Post by Dangertux on 2011-09-25
That's correct, that's port forwarding really all there is to it.

Keep in mind you won't be able to access the external IP from a machine inside your network (due to the way NAT routing works)

You can test to make sure the port is available to the outside world by using a site such as this [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If it shows port 22 is open you did it correctly.

---

### Post by DJKEMMET on 2011-09-25
> **Dangertux said:**
> That's correct, that's port forwarding really all there is to it.

Keep in mind you won't be able to access the external IP from a machine inside your network (due to the way NAT routing works)

You can test to make sure the port is available to the outside world by using a site such as this [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

If it shows port 22 is open you did it correctly.

so which IP address would I use? my 192.168.x.x or the 173.74.x.x?

by the way, thanks for this link i can see myself using it a lot, it's already book marked :PP

---

### Post by patryk77 on 2011-09-25
On step 2, I am confused by the "Source Port: 22" ...

Generally when firewalls mention "source ports" it means the Client needs to connect from port 22?

Which would mean tweaking the ssh client and having to run it as root.

If it doesn't work from an outside connection, try leaving the source port blank.

As you can see in the list below, it says: TCP Any-> (Number) for the other protocols. You want to add a "TCP Any -> 22" to the list, not "TCP 22 -> 22".

---

### Post by patryk77 on 2011-09-25
> **DJKEMMET said:**
> so which IP address would I use? my 192.168.x.x or the 173.74.x.x?

by the way, thanks for this link i can see myself using it a lot, it's already book marked :PP

You just need to enter port 22. It should automatically detect your IP (and it needs to use 173.74.x.x)

---

### Post by DJKEMMET on 2011-09-25
THANK YOU ALL SO MUCH!!!!!!

It Worked!!! I cannot thank you enough!!! I've been Trying to do this for a couple days now and you all helped me figure it out!!!! :D:D:D:D thank you thank you thank you! it's much appreciated!

---

### Post by patryk77 on 2011-09-25
Oops, sorry, I lied to you in the other thread.

Webmin is in fact not in the repos.

This will get you the newest version:
[http://glog.procrasstination.com/index.php?/archives/14-Installing-Webmin-on-Ubuntu!.html](http://glog.procrasstination.com/index.php?/archives/14-Installing-Webmin-on-Ubuntu!.html)

---

