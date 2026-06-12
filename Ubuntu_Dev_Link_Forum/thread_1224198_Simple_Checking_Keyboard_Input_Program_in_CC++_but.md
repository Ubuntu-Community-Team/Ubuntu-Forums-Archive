---
title: "Simple Checking Keyboard Input Program in C/C++ but with Strange Behavior!!"
date: 2009-07-27
forum: Ubuntu Dev Link Forum
---

### Post by GPUMan on 2009-07-27
Hi all,

I have a small function for checking whether the keyboard has been pressed without blocking. I tried to compile the program using g++ and another time with gcc. But nothing works correctly.

This is function 
```

int checkKeyboard() {
  fd_set readvec;
  struct timeval timeout;
  int ret, stdin_fd;

  timeout.tv_sec = 0;
  timeout.tv_usec = 0;
  stdin_fd = 0;
  FD_ZERO(&readvec);
  FD_SET(stdin_fd, &readvec);

  ret = select(1, &readvec, NULL, NULL, &timeout);
 
  if (ret == -1) {  // got an error
    if (errno != EINTR)  
      printf("select() error while attempting to read text input.\n");
    return FALSE;
  } else if (ret == 0) {
    return FALSE;  // select timed out
  }
  return TRUE;
}

```

This is the whole testing program :
```

#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#define TRUE 1
#define FALSE 0

//The previous code segment
int checkKeyboard() {
...
}
int main(int argc, char* argv[]) {
  int i;
  for (i=0; i<100000; i++) {
     if (vmd_check_stdin()>0) {
       printf("Keyboard was pressed. Terminating...\n");
       return 0;
     } else {
       printf("i = %d\n", i);
     }
  }
  return 0;
}

```

The program loops and exits when the user presses any key in the keyboard. When I run it, program loops and never exits although I pressed the keyboard multiple times while its counting!!After the program finish, the characters are printed to the console as if they all have been buffered while the program ran:confused:

Does anyone have an idea about this strange problem??

---

