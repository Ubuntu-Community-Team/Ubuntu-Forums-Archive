---
title: "C++ Serial Reading and Writing the Right Way"
date: 2013-10-26
forum: Ubuntu Application Development
---

### Post by orangeman555 on 2013-10-26
I'm loving Ubuntu! Its like it was made for developers!

I've gotten some very simplistic Serial writing code set up, but I know its definitely far from what it should be. See the below code. You can see that I've simply set up a permanent loop that asks for user input (this is just a test - every number is sent to a microcontroller which lights up an LED at a level of brightness corresponding to the number pushed).

This code *does* work, but I suspect opening and closing a port with every iteration is wasteful (especially if there was no delay!). Yet this simple example does work.

Basically **I'm looking for a valid way to interact with a serial port via C++**. Platform independent methods would be great, but I'm probably dreaming on that! 

```
#include <iostream>
#include <stdio.h>
using namespace std;

int main()
{
    cout << "test" << endl;

    int data[] = {1,2,3};  //Random data we want to send
    FILE *file;
     //Opening device file

    int getnum;
    int i = 0;

    while(true)
    {
        file = fopen("/dev/ttyACM0","w");
        cout << "Enter a number: " << endl;
        cin >> getnum;
        fprintf(file,"%d",getnum); //Writing to the file
        fclose(file);
    }

}
```

A class or library would be absolutely great. Or perhaps some simple guidelines. I'm fairly new to this, but I'm going to be doing LOTS of serial interaction, so I might as well get it right early on. 

Thanks!

---

