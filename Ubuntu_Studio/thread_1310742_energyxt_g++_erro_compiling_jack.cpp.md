---
title: "energyxt g++ erro compiling jack.cpp"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by dharmagio on 2009-11-02
hi
this is the 3rd post about ubuntu 9.10 in the same day, because this 9.10 is really messy.

my problem is that i am trying to get jack support for energyxt2
the instructions are:

1. download the sourcefile jack.cpp from [http://www.energy-xt.com/download/jack.cpp](http://www.energy-xt.com/download/jack.cpp) on your computer.

2. Open a terminal

3. In the terminal go to the folder, to which you downloaded jack.cpp

4. make sure that you have an c++-compiler (if you don't have one, type
sudo apt-get install g++
in the terminal

5. Make sure you have installed the alsa-sound- and jack-libraries, type
sudo apt-get install libasound2 libasound2-dev libjack0 libjack-dev

6. then compile the jack.cpp-file by typing
g++ -shared -lasound -ljack jack.cpp -o /_path_to_energyXT2_/libaam.so 

so after this it gives me this error:

jack.cpp:1: error: expected unqualified-id before &#8216;<&#8217; token

help please, because i never had this problem in other ubuntu releases.

___________________________________________________________________________________________
it was giving error in 64bit ubuntu
now i have 32bit so problem "solved"

---

