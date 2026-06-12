---
title: "library linking?"
date: 2009-05-23
forum: Ubuntu Dev Link Forum
---

### Post by gsciller3 on 2009-05-23
Hello. Im trying to program a lcd piece of hardware. I have compiled and installed the libraries in /usr/local/lib
  libusblcd.a   libusblcd.so    libusblcd.so.0.0.0
libusblcd.la  libusblcd.so.0  pkgconfig       
I created a simple program 

#include "usblcd.h"

int main(void)
{
    usblcd_operation *mylcd;
    /* init hid device and usblcd_operations structure */
    mylcd = new_usblcd_operations();
    /* init the USB LCD */
    mylcd->init(mylcd);
    /* sets backlight to on */
    mylcd->backlight(mylcd,1);
    /* close the USB LCD device */
    mylcd->close(mylcd);
    
    return 0;
}

And when compiling am getting

test.cpp: In function ‘int main()’:
test.cpp:5: error: ‘usblcd_operation’ was not declared in this scope
test.cpp:5: error: ‘mylcd’ was not declared in this scope

Any ideas? Thank you.

---

### Post by cmshowers on 2009-05-30
Hello gsciller3,

I assume you purchased the LCD from Mini-box.com since that is their sample source code you posted. The documentation on mini-box.com for the picoLCD hardware is a little sketchy (although they have great documentation for other products!). For other searchers who find this post, you can download the usblcd binaries from here:
[http://www.linuxconsulting.ro/picoLCD20x2/bin/](http://www.linuxconsulting.ro/picoLCD20x2/bin/)
or the source code from here:
[http://www.linuxconsulting.ro/picoLCD20x2/src/](http://www.linuxconsulting.ro/picoLCD20x2/src/)
I downloaded the source code and simply ran the autogen.sh script to install the necessary header and library files for working with the usb lcd. If there is an official link to these required library installation files somewhere, please post it in this thread.

That should bring us up to where you are having your problem, gsciller3. The first thing you're going to run into is the typo in that sample code from mini-box!  The ‘usblcd_operation’ was not declared error is because that is not the name of that struct. It should be ‘usblcd_operations’ (notice the s on the end).

Next you need to compile the sample code. Something like this should do:
gcc -o lcdtest lcdtest.c -lusblcd -lusb
Where your sample code is a file named lcdtest.c and your output binary will be named lcdtest. Notice that you need to link against both libusblcd and libusb. However, doing this created the following error for me:
./lcdtest: error while loading shared libraries: libusblcd.so.0: cannot open shared object file: No such file or directory
Which is particularly annoying since the file is sitting right there in the /usr/local/lib/ directory. A simple running of the command 'ldconfig' will clear this up (requires root).

This should get you on your feet and working with your LCD. The commands for the LCD are straight forward and have been problem free for me so far. Best of luck!

CS

---

