---
title: "2 troubles with Ubuntu server"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by josephmills on 2012-03-03
**EDIT**

sorry about the picture 1st. 
I got the virtual box to install thanks to some great people on the ubuntu+1 IRC channel. I hd to enable PAE_NX 
I will try to put up a better screen shot of enabling that. 
[http://s8.postimage.org/hk5y5gjf7/PAE.png](http://s8.postimage.org/hk5y5gjf7/PAE.png)

Still wondering about magneto thou. 




Hello there thanks for taking the time to read this you are awesome. 

So I am trying to install ubuntu 12.04 32bit server onto virtual box. everything looks good up to the point that I pick my english  and then press enter to install. This is where the error starts.  
this is what I get and it will not move past that. 

[http://imagebin.org/201807](http://imagebin.org/201807)
2nd I can not install magneto to a different ubuntu server. no matter how hard I try. Just wondering if other have magneto installed. If so How did you do it?   

Thanks let me know if there is anything that I can post to make this easy 
thanks

---

### Post by iponeverything on 2012-03-03
double check your uploaded screenshot - I am just seeing a 1x1 pixel image.

---

### Post by Dangertux on 2012-03-03
Are you using a 32 bit host operating system? If so you need to be using a 32 bit guest.

Also you may wish to try enabling PAE/nx in the vbox settings for that virtual machine as well as ioapic

Hope this helps

---

### Post by winh8r on 2012-03-03
> **josephmills said:**
> **EDIT**

sorry about the picture 1st. 
I got the virtual box to install thanks to some great people on the ubuntu+1 IRC channel. I hd to enable PAE_NX 
I will try to put up a better screen shot of enabling that. 
[http://s8.postimage.org/hk5y5gjf7/PAE.png](http://s8.postimage.org/hk5y5gjf7/PAE.png)

Still wondering about magneto thou. 




Hello there thanks for taking the time to read this you are awesome. 

So I am trying to install ubuntu 12.04 32bit server onto virtual box. everything looks good up to the point that I pick my english  and then press enter to install. This is where the error starts.  
this is what I get and it will not move past that. 

[http://imagebin.org/201807](http://imagebin.org/201807)
2nd I can not install magneto to a different ubuntu server. no matter how hard I try. Just wondering if other have magneto installed. If so How did you do it?   

Thanks let me know if there is anything that I can post to make this easy 
thanks

with regard to the second question, is that a typo? Are you actually having problems installing MAGENTO rather than magneto?

If so, I believe that there is a common issue discussed here:

[http://trandangkhoa.blogspot.com/2009/05/install-magento-on-ubuntu-problems-and.html]("http://trandangkhoa.blogspot.com/2009/05/install-magento-on-ubuntu-problems-and.html")

Hope this is of some help.

---

### Post by josephmills on 2012-03-06
Thanks guys and sorry that it took so long for me to respond. I have been busy. 

Dangertux thanks for the tips 

winh8r Took a look at that blog and am going to try it later on today. Will let you know. To be honest I have done all of what is suggested but change magento/app/code/core/Mage/Core/Model/Session/Abstract/Varien.php
so I look forward to that. 

thanks again guys

---

