---
title: "google deepdream"
date: 2015-07-28
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2015-07-28
I just installed google deepdream on Ubuntu 15.04. [http://www.slate.com/articles/technology/bitwise/2015/07/google_deepdream_it_s_dazzling_creepy_and_tells_us_a_lot_about_the_future.html](http://www.slate.com/articles/technology/bitwise/2015/07/google_deepdream_it_s_dazzling_creepy_and_tells_us_a_lot_about_the_future.html)

It is pretty cool but a bit slow since I don't have a Nvidia card and have to use cpu instead of CUDA and it is a netbook, but hey it works!

Step by step instructions for setting it up for Ubuntu [https://www.reddit.com/r/deepdream/comments/3cd1yf/howto_install_on_ubuntulinux_mint_including_cuda/](https://www.reddit.com/r/deepdream/comments/3cd1yf/howto_install_on_ubuntulinux_mint_including_cuda/)

However, if you just follow the guide it won't work. there are some additional steps.

Follow the guide to install the dependencies and set the environmental variables, he put the enviromental variables in .bashrc but alternatively you can create a file say, caff.conf, put it somewhere and run 

```
source /path/to/caffe.conf
``` before compiling caffe (and running deepdream)

Before compiling caffe change the file Makefile.config (in ~/caffe if you follow the guide) as follows:

Remove/comment out these lines
> 
INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include
LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib

Then add these
> 
INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
LIBRARY_DIRS := $(PYTHON_LIB) /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial/


(if you can't use CUDA also uncomment line8 CPU_ONLY :=1 as described in the guide and there is an additional step for multicore  also in the guide)

Now Caffe should build. After that create a symblink (assuming the caffe directory is in your home)
```
sudo ln -s  /home/username/caffe/python/caffe /usr/local/lib/python2.7/dist-packages/caffe
```

Finally there are some dependencies which the system versions don't work apparently, so you have to get the latest
```
sudo pip install protobuf
sudo pip install scikit-image
```

Now everything should work. Some modifications and additional steps to the guide may be needed for setting up CUDA, but I don't know since I don't have a Nvidia card.

Enjoy. :)

---

### Post by NathanRodriguez on 2015-07-28
Interesting AI technology... What have you been creating with it ?

---

### Post by monkeybrain20122 on 2015-07-29
Nothing much so far. I am travelling and have brought only my netbook (it is not as slow as I expected, in fact going quite smooth) so just ran a few examples to make sure that it works. I grabbed an image of some woman's face and generated the image attached. :) I am learning machine learning and python so this is definitely very interesting for me.

---

