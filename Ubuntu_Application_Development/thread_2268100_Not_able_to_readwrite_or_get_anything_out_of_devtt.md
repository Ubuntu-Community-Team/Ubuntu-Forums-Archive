---
title: "Not able to read/write or get anything out of /dev/ttyACM0 device file"
date: 2015-03-06
forum: Ubuntu Application Development
---

### Post by sachi0091 on 2015-03-06
Hi all,

  I'm currently doing an open source project and i'm struck in this very problem.

  I have a **microcontroller** and i'm using **ubuntu 14.04 LTS OS**.

  when ever i connect the microcontroller to the system **/dev/ttyACM0** is the device file for the connected microcontroller.

  and i'am trying to have a serial communication with the device via /dev/ttyACM0 file.

  but the problem here is i'm not able to read/write the device file ( like sudo tail /dev/ttyACM0 will hang and the size of this file remains 0bytes even after i write something to it ).

  i have googled and roamed around so many forums for about 2 weeks but still i'm unable to find any solutions.

  here is the snapshot of dmesg | grep ttyACM0 command 

  **[  198.868233] cdc_acm 1-2:1.0: ttyACM0: USB ACM device**

  and i have changed the permission of the file too using 

  **sudo chmod 777 /dev/ttyACM0.**

  here is the output of ls -l command 
  
  **crw-rw-rw- 1 root dialout 166, 0 Mar  6 15:00 /dev/ttyACM0**

  and here goes my program to open the character special device file (/dev/ttyACM0). 

  [I]int init_uart(const char *file){ // input is /dev/ttyACM0

    int fd;    // File descriptor for the port
    fd = open(file, O_RDWR | O_NOCTTY | O_NDELAY);

    if (fd == -1){
        fprintf(stderr, "init_uart: Unable to open %s -- %s\n",file,strerror(errno));
        exit(EXIT_FAILURE);
    }

    //fcntl(fd, F_SETFL, FASYNC);
    //fcntl(fd, F_SETFL, FNDELAY);
    fcntl(fd, F_SETFL, O_ASYNC|O_NONBLOCK|fcntl(fd, F_GETFL));
    FD_SET(fd, &readfs);
    return (fd);
  }[/I]

  Any help is appreciated.:popcorn:

---

