---
title: "Completly in Ubuntu."
date: 2008-05-03
forum: Testimonials &amp; Experiences
---

### Post by RRosset on 2008-05-03
I moved from M$ to Ubuntu about 4 months ago when i came back from the south (i live in Argentina) i changed my mind in many ways, and found that Ubuntu fits that need. So here I am. With no doubt I backup most of my documents and erase with M$. My desktop computer received ubuntu with no problems at all. But my laptop no. First a problem with wireless, then with my orbital webcam. Anyways, it took me 4 months till i finally installed the bloody webcam. Now i'm 100% in both machines in Linux. I'm still not an expert. But i'm totally happy with my both computers running in ubuntu. And i wanna share my moment with you guys! hhehehehe anyways, keep in touch.

Btw, My laptop is an Aspire 5570Z jic someone needs some help installing something.

Bob :guitar:

---

### Post by acelin on 2008-05-03
You got the cam to work? Dude- I have been trying for a while ( although not too hard) and cant get it to work. I have an Aspire 5100...

---

### Post by RRosset on 2008-05-05
Ok Acelin, I know this is in some other thread. But I can't find if. So here we go:

First you should check your orbicam is installed and recognized:
In your terminal, type:
```
lsusb
```

Now you have to download something to compile the module (honestly I don't know what I'm saying, I'm just translating an spanish article, translated from an italian one!, but i followed it and here i am!)

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Now the source, and then uncompress
```
wget http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz
tar zxvf gspcav1-20071224.tar.gz
cd gspcav1-20071224
```

After that, we... COMPILE!
```
make
sudo make install
```

We must load the module so we:
```
sudo gedit /etc/modprobe.d/options
```

Inside the file we add this line at the end of the file:
```
options gspca force_rgb=0 
```

Then we type:
```
sudo modprobe gspca
```

Finally. Let's take a look and see what the heck we did.
```
ls /dev/video*
dmesg|tail -30
```

*note /dev/video0 was in my case

Ok. We should be OK here. I found some problems using camorama, but the other site suggested Cheese, and since I love cheese (my mom used to say that so much cheese will make willy cry... but for the moment, I'm fine!).
Anyways, i'm missing the point. Now. We need to install cheese! so... here we go.

```
sudo apt-get install cheese
```

That's it! Hope this little step by step guide help you solve your webcam issue dude.

Don't hesitate to pm me if you need further information. Later!

Bob

---

