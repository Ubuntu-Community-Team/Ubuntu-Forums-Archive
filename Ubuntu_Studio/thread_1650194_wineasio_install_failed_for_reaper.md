---
title: "wineasio install failed for reaper"
date: 2010-12-21
forum: Ubuntu Studio
---

### Post by lastcigaretteme on 2010-12-21
Hello all,
I'm having trouble getting wineasio to install properly. I'm hoping to run Reaper on my Ubuntu Studio system. I'm a relative noob running Ubuntu Studio on Ubuntu 8.04, Hardy Heron, with Kernel Linux 2.6.24-rt, on an Acer Aspire 5100 laptop. Hardware has 2.2 GB memory and processor is AMD Turion 64 Mobile Technology MK-38.

I followed directions from here [http://www.associatedcontent.com/article/2760075/make_music_for_free_with_reaper_and.html?cat=33](http://www.associatedcontent.com/article/2760075/make_music_for_free_with_reaper_and.html?cat=33)  and here  [http://forum.cockos.com/archive/index.php/t-39376.html](http://forum.cockos.com/archive/index.php/t-39376.html) . Installed Wine, which seems to be working fine. Downloaded wineasio and asiosdk (actually asiosdk2.2), unzipped them and copied 'asio.h' file to wineasio folder. Tried to install it with this:

make

sudo make install

regsvr32 wineasio.dll


Here's what happened in Terminal:

launie@laptop:~$ cd Desktop/wineasio
launie@laptop:~/Desktop/wineasio$ make
pkg-config --exists jack
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
asio.c: In function ‘__wrapped_IWineASIOImpl_init’:
asio.c:608: warning: implicit declaration of function ‘jack_client_real_time_priority’
asio.c: In function ‘__wrapped_IWineASIOImpl_start’:
asio.c:768: warning: assignment discards qualifiers from pointer target type
asio.c:800: warning: assignment discards qualifiers from pointer target type
asio.c: In function ‘__wrapped_IWineASIOImpl_controlPanel’:
asio.c:1194: warning: initialization discards qualifiers from pointer target type
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o main.o main.c
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o regsvr.o regsvr.c
winegcc -m32 -shared wineasio.dll.spec -mnocygwin -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -loleaut32 -lwinspool -lwinmm -lpsapi -lpthread -luuid
asio.o: In function `__wrapped_IWineASIOImpl_init':
/home/launie/Desktop/wineasio/asio.c:608: undefined reference to `jack_client_real_time_priority'
collect2: ld returned 1 exit status
winegcc: i486-linux-gnu-gcc failed
make: *** [wineasio.dll.so] Error 2
launie@laptop:~/Desktop/wineasio$ sudo make install
cp wineasio.dll.so /usr/lib/wine/
cp: cannot stat `wineasio.dll.so': No such file or directory
make: *** [install] Error 1
launie@laptop:~/Desktop/wineasio$ regsvr32 wineasio.dll

Though I suspected that something hadn't worked properly, I forged ahead, installing Reaper from the .exe file, and adjusting jack preferences.
Then, after failing to get reaper to work properly (it gives an error saying that I have no asio driver), I decided that the terminal message above did indeed indicate that wineasio and asiosdk2 had not installed/compiled correctly. I tried terminal again, with these results:
launie@laptop:~$ cd Desktop
launie@laptop:~/Desktop$ cd Desktop/wineasio
bash: cd: Desktop/wineasio: No such file or directory
launie@laptop:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
launie@laptop:~/Desktop$ cd Desktop/wineasio
bash: cd: Desktop/wineasio: No such file or directory
launie@laptop:~/Desktop$ 

Wish I could just back up and do it right the first time. But that boat has sailed. I'm hoping someone can suggest ways to fix this. Thanks in advance for any suggestions.

I also read through this post [http://ubuntuforums.org/showthread.php?t=1294645&highlight=wineasio+reaper](http://ubuntuforums.org/showthread.php?t=1294645&highlight=wineasio+reaper)  in hopes of finding a solution, but most of this either went over my head or didn't seem relevant to my issue. Apologies if I overlooked other relevant posts.

---

