---
title: "ubuntu 9.10 problem in  C library files"
date: 2009-12-22
forum: Ubuntu One (CLOSED)
---

### Post by clinus on 2009-12-22
HI, 
I'm using ubuntu 9.10 and I'm trying to run c programs but it show something file missing, I'm pasting them here,
Can any one help me how to solve this? what to do?

gcc helo.c
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

---

### Post by lewisforlife on 2009-12-23
Try installing build-essential, open a terminal, and type:

```
sudo apt-get install build-essential
```

---

### Post by clinus on 2009-12-23
sudo apt-get install build-essential its not working for tat, still missing somthing

---

### Post by lewisforlife on 2009-12-24
> **clinus said:**
> sudo apt-get install build-essential its not working for tat, still missing somthing

Are you getting an error message when you run sudo apt-get install build-essential?  Can you paste the message you are getting in this forum, and I should be able to help you troubleshoot this.

---

### Post by clinus on 2009-12-24
No, I've installed build-essential but when I compile I'm getting errors, I'm pasting them here

c-nna@c-nna-lapy:~$ sudo apt-get install build-essential                        
[sudo] password for c-nna:                                                      
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
build-essential is already the newest version.                                  
The following packages were automatically installed and are no longer required: 
  gcc-4.3-base libclamav6 libtommath0 cpp-4.3                                   
Use 'apt-get autoremove' to remove them.                                        
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.  


c-nna@c-nna-lapy:~$ gcc helo.c
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

same thing with cc -o commands, It is generating .o files but unable to create executable file,

I've no Idea how to proceed,

---

### Post by lewisforlife on 2009-12-24
Hmm... Try installing libc6-dev

```
sudo apt-get install libc6-dev
```

If that doesn't work, please post your source code so that I can take a look at it and see if there is some kind of problem with the code.

---

### Post by clinus on 2009-12-24
I've tried that also, but still same prob, Source file is running under windows no prob with source file, I'm pasting that here,

Source:

#include<stdio.h> 
 
main() 
{ 
      int input; 
      int i,j,k,s,count=1; 
      j=1; 
      printf("Plz enter the Number to draw hollow Square: "); 
      scanf("%d", &input); 
      printf("\n******************\n"); 
      for(i=0;i<input;i++)//this will print top row hollow square 
      { 
        printf("*"); 
      } 
      printf(" "); 
       
      for(i=1;i<input;i++){//this is to print left and right sides of the square 
        printf("\n*"); 
           for(j=2;j<input;j++) 
             printf(" "); 
             printf("*"); 
      } 
      printf("\n"); 
      for(i=1;i<=input;i++)//this will print bottom of the square 
      { 
        printf("*"); 
      } 
       
      getch(); 
}

commands I used to compile: gcc fileName.c and cc -c fileName.c.
gcc fileName.c is not working displaying the same thing, but cc -c fileName.c is working and generating .o file. but from here unable to move forward.
show me the way how to proceed what commands to use compile and run.

---

### Post by lewisforlife on 2009-12-26
All-the-way at the bottom of your program, you have a call to a function, getch(), this is an undefined function, this function does not exist.  There is a function in stdio.h called getchar() though, is that what you wanted to use?  Try changing getch() to getchar() and it should work fine.  I compiled your program with:

```
gcc fileName.c -o fileName
```

Let me know if you have any other issues.

---

### Post by clinus on 2009-12-27
I'm bad to bring again, source code is not-at all a problem, even its not working to print hello-world.  My question is how do I troubleshoot this problem? when I tried to compile it is saying that -lc  can not find, what does it mean Whats wrong with the library files. I've un-installed all the build-essential and libc6-dev and installed again but same thing repeating.

if gcc is the same as cc, then why cc is generating .o file and if I use gcc it is saying can not find -lc, what does it mean?.

I'm using Ubuntu 9.10.
This is what I'm getting while compiling:

Same programs are working under different environment like Windows
c-nna@c-nna-lapy:~/Desktop$ gcc -o heloworld heloworld.c
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

Thanks

---

### Post by lewisforlife on 2009-12-27
This is a strange problem.  It sounds like you do not have libc6-dev installed, even though you have installed it.  What do you get if you run:

```
locate stdio.h
```

---

