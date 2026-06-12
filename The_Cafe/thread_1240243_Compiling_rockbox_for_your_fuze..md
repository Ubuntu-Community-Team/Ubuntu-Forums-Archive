---
title: "Compiling rockbox for your fuze."
date: 2009-08-14
forum: The Cafe
---

### Post by dragos240 on 2009-08-14
Hi everyone!

A while back I posted a topic on how to get firmware for your sansa fuze, all I provided was pre-compiled binaries. And to get the latest version you'd have to wait for someone else to compile it for you. Well, I felt that you should know how to get and compile the latest sansa fuze firmware anytime you want!

Okay, read below. And remember, this will only work on a sansa fuze v1.

Make sure you have subversion as you will need it to get the latest revision source. When you have subversion, open up a terminal and paste this in:
svn co svn://svn.rockbox.org/rockbox/trunk rockbox

This will create a directory called "rockbox" inside your home folder. To navigate into it do this:
cd rockbox

Then create a new folder called 'build', to do this. Paste the following into your teminal:
mkdir build

Now you will need a custom compiler, to get this custom compiler navigate into the tools directory:
cd tools

And then run
sudo -s

And then ./rockboxdev.sh

Type 'a' and hit hit return

Wait for this as it might take a while.

Now assuming you use BASH and the script has finished, as these 2 lines to your .bashrc file:
PATH=$PATH:/usr/local/arm-elf/bin
export PATH

logout and log back in.
 
Now before we configure and compile we will need SDL and SDL-devel. Get them from your local repository. Now get into your rockbox/build directory and run:
../tools/configure

and then select 58, press enter.

and now type n and press enter.

This should generate the makefile.

now simply type:
make

This will take a while also.

After this completes, you will want to zip this inside an archive. Do this:
make zip

this should not take long cat all.

Now move rockbox.zip to your home directory by doing this:
mv rockbox.zip ~

Delete everything in the build directory, do this how you wish.

and now run 
../tools/configure

this time select 'b' for bootloader and hit enter.

Now make by:
make

after this completes, navigate back a step and into rbutil:
cd ..
cd rbutil

now to go to mkamsboot:
cd mkamsboot

copy the bootloader-fuze.sansa into this directory, along with the original firmware. You can get the original firmware from [here]("http://mp3support.sandisk.com/firmware/fuze/fuze01.02.26.zip").

Now once all 2 of those files are inside the mkamsboot directory, you will want to make:
make

and now run ./mkamsboot fuzeA.bin bootloader-fuze.sansa output.bin

and rename output.bin to fuzea.bin by:
mv output.bin fuzea.bin

Finally copy the fuzea.bin (make sure it's fuzea.bin not fuzeA.bin, linux is case sensitive.) inside your fuze. Now last but not least, unzip the contents of rockbox.zip into your fuze, and reboot the fuze. Enjoy your new rockbox.

---

### Post by dragos240 on 2009-08-15
Bump. If anyone wants it.

---

### Post by clonne4crw on 2009-08-15
Good job.

---

