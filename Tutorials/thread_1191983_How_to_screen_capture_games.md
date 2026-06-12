---
title: "How to screen capture games"
date: 2009-06-19
forum: Tutorials
---

### Post by curvedinfinity on 2009-06-19
I had to screen capture my own OpenGL application a while ago, and it was a real pain in the butt to do on Linux. There are plenty of programs that screen capture from the X buffer, but that is very processor-intensive and slow. However, I did find one option that actually captures directly from the graphics card: Yukon.

Yukon is fairly straight forward, but is relatively new, so it doesn't have any install packages or GUIs.

[LIST=1]
[*]Get the dependencies:
```
sudo apt-get install build-essential subversion yasm mencoder libasound2-dev libgl1-mesa-dev
```
[*]Get the source (make sure to accept the certificate):
```
mkdir yukon
cd yukon
svn co https://devel.neopsis.com/svn/seom/branches/packetized-stream seom
svn co https://devel.neopsis.com/svn/yukon/branches/rewrite yukon
cd seom
./configure && make && sudo make install
cd ../yukon
./configure && make && sudo make install

```
[*]Install the yukon config files:
```

sudo mkdir -p /etc/yukon/system
sudo cp sysconfig /etc/yukon/system/default
mkdir ~/.yukon
cp tools/yukon.conf ~/.yukon/conf

```
[*]Edit the preference file:
```

gedit ~/.yukon/conf

```
Change
```

# OUTPUT = file:///tmp/yukon.seom

```
to
```

OUTPUT = file:///home/<your user>/Desktop/recording.seom

```
[*]Run your app through yukon:
```

yukon glxgears

```
[*]Press F8 to start recording and F8 again to stop.
[/LIST]

Now you should have a recording.seom file on your desktop. To convert this to a usable filetype, use yukon's tool:

[list=1]
[*]Convert the seom file to a y4m file using yukon's tool:
```

./filter ~/Desktop/recording.seom > ~/Desktop/recording.y4m

```
[*]Convert the y4m to mpg with mencoder:
```

mencoder ~/Desktop/recording.y4m -of mpeg -ovc lavc -lavcopts vcodec=mpeg1video -oac copy -o ~/Desktop/recording.mpg

```
[/list]

Hopefully this works for everyone. There may be some dependencies I forgot about, so please report back.

---

### Post by gershon on 2009-10-07
great post man, one small comment, to make it work here i need to execute
[INDENT]`sudo ldconfig`[/INDENT]
after installing the compiled libs

---

### Post by riking on 2012-07-16
The author has moved his code to Github.
As such, you need to change these lines in installation (Step 2):
```

svn co https://devel.neopsis.com/svn/seom/branches/packetized-stream seom
svn co https://devel.neopsis.com/svn/yukon/branches/rewrite yukon

```

To these:
```

git clone https://github.com/wereHamster/seom.git
git clone https://github.com/wereHamster/yukon.git

```

If necessary, `sudo apt-get install git` first.

---

