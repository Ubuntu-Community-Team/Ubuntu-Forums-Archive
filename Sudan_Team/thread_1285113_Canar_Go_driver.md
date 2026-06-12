---
title: "Canar Go driver"
date: 2009-10-07
forum: Sudan Team
---

### Post by zero-n on 2009-10-07
This is a step by step guide to install Canar go driver in ubuntu 9.04 (jaunty)


1- Plug in your modem.
2- Ubuntu will recognise it as a CD & flash memory.
3- Open the terminal & copy this file [COLOR="Red"]**RDEVCHG**[/COLOR] from the cd.
```
cp /media/cdrom0/Linux/RDEVCHG /home/zero/Desktop/
```
you need to change [COLOR="Red"]zero[/COLOR] to your home folder name & you may need [COLOR="Red"]cdrom0[/COLOR] to Canar_Go

4- Go to you desktop or the location where you copy th file
```
cd Desktop/
```

5- Give the installation script the execution privilege 
```
sudo u+x RDEVCHG
```

6- Run the installation script
```
sudo ./RDEVCHG
```
it will give you the following output
```
RDEVCHG Linux Version : 1.0
Please, Wait!
Bus 003 Device 003: ID 16d8:680a CMOTECH Co., Ltd. 
...
Success SwitchMode.
*** stack smashing detected ***: ./RDEVCHG terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7fcada8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7fcad60]
./RDEVCHG[0x80486f7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7ee3775]
./RDEVCHG[0x80484c1]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:07 7349       /home/zero/Desktop/RDEVCHG
08049000-0804a000 rw-p 00000000 08:07 7349       /home/zero/Desktop/RDEVCHG
089bb000-089dc000 rw-p 089bb000 00:00 0          [heap]
b7ecc000-b7ecd000 rw-p b7ecc000 00:00 0 
b7ecd000-b8029000 r-xp 00000000 08:07 2657       /lib/tls/i686/cmov/libc-2.9.so
b8029000-b802a000 ---p 0015c000 08:07 2657       /lib/tls/i686/cmov/libc-2.9.so
b802a000-b802c000 r--p 0015c000 08:07 2657       /lib/tls/i686/cmov/libc-2.9.so
b802c000-b802d000 rw-p 0015e000 08:07 2657       /lib/tls/i686/cmov/libc-2.9.so
b802d000-b8030000 rw-p b802d000 00:00 0 
b8031000-b803e000 r-xp 00000000 08:07 2601       /lib/libgcc_s.so.1
b803e000-b803f000 r--p 0000c000 08:07 2601       /lib/libgcc_s.so.1
b803f000-b8040000 rw-p 0000d000 08:07 2601       /lib/libgcc_s.so.1
b8040000-b8043000 rw-p b8040000 00:00 0 
b8043000-b8044000 r-xp b8043000 00:00 0          [vdso]
b8044000-b8060000 r-xp 00000000 08:07 8001       /lib/ld-2.9.so
b8060000-b8061000 r--p 0001b000 08:07 8001       /lib/ld-2.9.so
b8061000-b8062000 rw-p 0001c000 08:07 8001       /lib/ld-2.9.so
bf94d000-bf962000 rw-p bffeb000 00:00 0          [stack]
```

7- The installation phase is done in the notification area you click right click on the network icon & select [COLOR="Red"]Edit connection[/COLOR] the move to the Mobile [COLOR="Red"]Broadband[/COLOR] tab you will find a connection named [COLOR="Red"]Auto Mobile Braodband CDMA connection[/COLOR] choose it and click [COLOR="Red"]Edit[/COLOR] it will ask you about the root password enter it.

8- Enter you username & password & click [COLOR="Red"]apply[/COLOR] you can change the connection name if you like.

now in the notification area press a left mouse botton on it & choose
[COLOR="Red"]Auto mobile broadband CDMA[/COLOR] connection or the connection that you have specified.

unfortunately you need to do these steps every time you turn-off the system.


**[SIZE="5"]Another way to do it[/SIZE]**:
This way is permanent so you don't need to do it again every time you turn-off your system but it have a little problem you must have an Internet connection cause the package we want to install have dependencies so you may run the first way for one time and connect to the Internet & this do this way to have a permanent driver.

1- download cmotech-qt package from [_**[COLOR="Red"]here[/COLOR]**_]("http://www.4shared.com/file/133986371/74edf4f0/cmotech-qtmodem_19_all.html")
2- install the package
3- Run the program from  application => Internet => C-motech
4- Specify you username & password 

Now you have a Cmotech driver (Canar GO driver) installed in your system.

:popcorn:

---

