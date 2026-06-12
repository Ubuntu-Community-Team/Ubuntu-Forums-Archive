---
title: "C++ : how to implement SANE"
date: 2021-09-18
forum: Ubuntu Application Development
---

### Post by pol2095 on 2021-09-18
hello,

I'm trying to implement the SANE library under Ubuntu by following this [example]("https://gist.github.com/StefanoBelli/fb65543553ce48dbd2744c513b3935e2"), it work but I would like to detect if a scanner has a document feeder and how to select it, I am also looking an example to retrieve the image in jpeg and not in [pnm]("https://yushulx.medium.com/a-simple-c-program-to-access-scanner-on-linux-with-sane-561f50d3bf35")?

Thanks

---

### Post by TheFu on 2021-09-18
Did you pull the sane-dev package with the source code?  Is there a libsane-dev package?  Why re-invent this wheel?  If it were me, I'd leverage what other people have already done and just build the specific stuff on the earlier tools for my specific needs.

The supported image formats will depend on the hardware.  You can convert those to any other format you like. There are lots of tools to do that.  **convert** (that's the program name), from the image-magick suite comes to mind. Any conversions can be hidden from the users.

---

### Post by mIk3_08 on 2021-09-18
> **pol2095 said:**
> hello,
I'm trying to implement the SANE library under Ubuntu by following this [example]("https://gist.github.com/StefanoBelli/fb65543553ce48dbd2744c513b3935e2"), it work but I would like to detect if a scanner has a document feeder and how to select it, I am also looking an example to retrieve the image in jpeg and not in [pnm]("https://yushulx.medium.com/a-simple-c-program-to-access-scanner-on-linux-with-sane-561f50d3bf35")?
Thanks

Hi I am using Xsane in my printer/scanner device under Linux Ubuntu 18 Operating System and it works smoothly. 
I am able to use jpeg format when I perform a scan to any of my documents. You just have to select some image 
format under xsane applications. I am not using any application software to convert some images that I get from 
my scanned document. Good luck and regards.

---

### Post by pol2095 on 2021-09-18
It's for integrate sane in my app, I don't need to use an other app...
> // SANE API usage example
// link against libsane
//  --> [http://www.sane-project.org/html/doc012.html](http://www.sane-project.org/html/doc012.html)
#include <sane/sane.h>
#include <stdio.h>


int main() {
    //
    // Initialize SANE 
    //
    SANE_Int version;
    sane_init(&version, NULL);
    
    //
    // Request SANE backend to perform device lookup
    // and retrieve a list
    //
    SANE_Device** devices;
    sane_get_devices((const SANE_Device***)&devices, 0);


    do {
        printf("found: %s\n", (*devices)->vendor);
    } while(*(++devices));


    devices--;
    
    //
    // Open selected devices, get an handle to that
    //
    SANE_Handle hnd;
    sane_open((*devices)->name, &hnd);
    
    //
    // Start scanning
    //
    sane_start(hnd);
    
    
    //
    // Read scanning data
    //
    SANE_Int len;
    SANE_Byte data[1024];
    sane_read(hnd, data, 1024, &len);


    printf("%d\n", len);
    
    //
    // We're done, cleanup...
    //
    sane_exit();
    
    return 0;
}


I need to convert "data" to jpeg ?

---

### Post by pol2095 on 2021-09-19
I managed to make it work with the flatbed, but not using the feeder
> SANE_Parameters params.lines the feeder return a value 1100 (817 for the flatbed), it's the same page, the scanner display "scanning in progress" and the app crash ?

---

### Post by pol2095 on 2021-09-20
I find a workaround.

---

### Post by TheFu on 2021-09-20
> **pol2095 said:**
> I find a workaround.

Is it a big secret?  Please share.

---

