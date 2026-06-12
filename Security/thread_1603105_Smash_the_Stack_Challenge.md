---
title: "Smash the Stack Challenge"
date: 2010-10-22
forum: Security
---

### Post by type8code0 on 2010-10-22
I was wondering is there anyone here ever try Smash the Stack challenge? You can find the challenge here.

Try the challenge here
[http://www.smashthestack.org/wargames.php](http://www.smashthestack.org/wargames.php)

> General questions:


How do I ask a question?
What is Smash the Stack?
How do I connect to the Wargames?
How do I get the password for the next level?
I'm connected now what?
What operating systems do I need to play?
What is the goal of the games?
Where do I go if I need help?
I keep getting permission denied. What's up?
How can I contribute a wargame level?
Can I try to get root?
I can't connect. What's wrong?
Can you help me?
What is PuTTy and where do I get it?
How do I connect to IRC?
How do I add a tag?
I signed up to the forum, but I did not get a confirmation email.


What is Smash the Stack?

The Smash the Stack Wargaming Network hosts several Wargames. A Wargame in our context can be described as an ethical hacking environment that supports the simulation of real world software vulnerability theories or concepts and allows for the legal execution of exploitation techniques. Software can be an Operating System, network protocol, or any userland application. 


How do I connect to the Wargames?

To connect to any of the Wargames you need an ssh client (openssh, PuTTy, SecureCRT). Each game has it's own set of connection details. You need to pay attention to the port and initial username. If you are using a unix variant simply type the following at the shell prompt: 
user@box:$ ssh -l level1 io.smashthestack.org -p2224
when you are prompted for the password enter "level1" without the quotes. This information is also provided on the `io' wargame page. Once you are logged in read the text (MOTD: Message of the day) that is displayed on your screen. 


How do I get the password for the next level?

The password for each level is located in different places depending on the game, but it will be located in one of the following locations:
~/.pass
~/passwd
/pass/
the MOTD will specify exactly where it is located for each game. To view it simply use /bin/cat
user@box:$ cat ~/.pass
user@box:$ cat /pass/level1
user@box:$ cat ~/passwd



I'm connected now what?

Celebrate! \o/ 


What operating system do I need to play?

Any OS will do. Windows, Linux, BeOS, MacOS, BSD, or VMS. 


What is the goal of the games?

The goal of the games is for you to get from the first level to the (current) last level. Along the way you should pickup or refine any techniques that were required to defeat the level. The levels for each game are structured progressively. You start at the first level. Once you have completed the first level you will have the credentials to view the password for the next level. This is the same for all the games. To view your current credentials or userid type the following at the shell prompt:
user@box:$ id
the text that is returned is your current user level status. 


Where do I go if I need help?

If you need help with a topic not covered in this FAQ you can utilize one of the following resources:

CGIIRC
FORUM
EMAIL
GOOGLE


I keep getting permission denied. What's up?

blah


How can I contribute a Wargame level?

If you want to contribute a level to any of the StS games send the level and exploit to [email]staff@smashthestack.org[/email]


Can I try to get root?

The focus of the games is not to get root, but you are welcome to try, if you manage to escalate your privileges to the superuser, we ask that you do not wreak havoc, instead we would appreciate an an email to [email]staff@smashthestack.org[/email] notifying us of the deficiency so we can correct it.


I can't connect. What's wrong?

No internet connection mebe?


Can you help me?

No. See How do I ask a question?


What is PuTTy and where do I get it??

PuTTy is a terminal emulator application that can act as a client for various protocols including SSH. It can be download here


How do I connect to IRC?

To connect to IRC you need and IRC client. We provide a webbased IRC client (CGIIRC) that you can use or you can download mIRC. If you are using linux, but have limited experience you can use xchat.


How do I add a tag?

Each level has a sub directory called public_html under the respective home directory. Inside that public_html directory is a file called index.html or tags.html. To add your tag simply use redirection...
user@box:$ echo "stacksmasher3 was heRe" >> ~/public_html/index.html 


Why did I not receive a confirmation email from the forum?

You probably entered the Captcha wrong. Try again. If you still cannot register contact us at [email]staff@smashthestack.org[/email] or join #staff and notify us of the issue.
[http://www.smashthestack.org/faq.php](http://www.smashthestack.org/faq.php)

---

### Post by Dimitris1989 on 2011-03-24
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/stat.h>
#include <fcntl.h>

#define MAX_ADDR_LEN 128

#define ADDR_LENGTH_OFFSET 4
#define ADDR_OFFSET 8

typedef unsigned char shsize_t;

typedef struct{
  char addr[MAX_ADDR_LEN];
  shsize_t len;
} arp_addr;

void
print_address(char *packet)
{
  arp_addr hwaddr;
  int i;

  hwaddr.len = (shsize_t) *(packet + ADDR_LENGTH_OFFSET);;
  memcpy(hwaddr.addr, packet + ADDR_OFFSET, hwaddr.len);
  
  printf("Sender hardware address: ");
 for (i = 0; i < hwaddr.len - 1; i ++)
    printf("%02hhx::", hwaddr.addr[i]);
  printf("%02hhx\n", hwaddr.addr[hwaddr.len - 1]);  
  
  return;
}

int main(int argc, char *argv[])
{
  struct stat sbuf;
  char *packet;
  int fd;

  if (argc != 2){
    printf("Usage: %s <packet file>\n", argv[0]);
    return EXIT_FAILURE;
  }

  if ((stat(argv[1], &sbuf)) < 0){
    printf("Error opening packet file\n");
    return EXIT_FAILURE;
  }

  if ((fd = open(argv[1], O_RDONLY)) < 0){
    printf("Error opening packet file\n");
    return EXIT_FAILURE;
 
  if ((packet = (char *)malloc(sbuf.st_size * sizeof(char))) == NULL){
    printf("Error allocating memory\n");
    return EXIT_FAILURE;
  }

  if (read(fd, packet, sbuf.st_size) < 0){
    printf("Error reading packet from file\n");
    return EXIT_FAILURE;
  }
  close(fd);
  print_address(packet);
  free(packet);
  return EXIT_SUCCESS;
}

}
```

The code above has a buffer overflow problem. I have succeeded fixing it by using gdb. What i would like to know is if there is a way to "smash the stack" using enviroment variables and commands.For example...


```
dimitris@dimitris-VirtualBox:~$ SHELL="/bin/bash"
dimitris@dimitris-VirtualBox:~$ export SHELL
```

Thanks for any help....

---

### Post by Dimitris1989 on 2011-03-24
This might not be the right thread to ask for this, so please if i shouldn't have post here someone show me a link for the appropriate thread..thnx

---

### Post by bodhi.zazen on 2011-03-25
I closed this thread as it is an old thread, almost a year old and we really do not support this kind of activity here.

By that I mean it is not directly Ubuntu support and the information can easily be misused / used for malicious purposes.

If you google you should be able to find a more appropriate site for this kind of activity.

---

