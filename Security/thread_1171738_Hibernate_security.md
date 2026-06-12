---
title: "Hibernate security"
date: 2009-05-27
forum: Security
---

### Post by ivze on 2009-05-27
Recently, i was thinking about global things, and found a question, i could not answer. Imagine, i am running some process (e.g. encfs), that holds some valuable secret data (in case of encfs that would be partition key). Let's now ask Ubuntu to hibernate. The memory contents will be dumped to swap partition, so that they can be restored afterwards. Undoubtedly, if the computer is a notebook and it gets stolen when hibernated, the key will be lost. However, i wonder, whether some data stays on swap partition after restoring back from it. I mean, is swap anyhow purged after resuming system. If not, this could be exploited, especially if the system has much memory and don't use swap.

Thanks in advance!

---

### Post by ivze on 2009-05-28
Ding! 8]

---

### Post by ivze on 2009-05-29
Answering to myself 8).
[https://answers.launchpad.net/ubuntu/+question/61140/?loggingout=1](https://answers.launchpad.net/ubuntu/+question/61140/?loggingout=1)
The post has a significant statement:
> Swap is Completely ERASED on every shutdown/restart, and all posible data in there is permanently deleted.
This means, nothing is left on swap, when computer shuts down, including possible hibernation-related data.

---

### Post by ivze on 2009-05-29
Achtung! 0_0

After making this post, i felt a bit suspicious and decidet to find out myself, whetres swap is cleaned at shutdown.

To find it out, i wrote a little c program, that put 1000 copies of a given string into memory. The source is attached. It can be compiled by calling > gcc tsd.c -o tsd.

Using Ubuntu 9.04, i launched the program with "MegaTopSecret" parameter. It put the string into memory and hang on terminal waiting for any key to be pressed. 

I hibernated the system, this caused the whole memory being put to swap. Our string was put there to.

I restored then, pressed "any key", making the "tsd" program finish. After that i shut the computer down.

I took a liveCD with 9.04, booted into it. It found swap and decioded to use it for swapping, so i had to use
> sudo swapoff -a.

After that, i started (my swap partition is on sda3)
> sudo dd if=/dev/sda3 | hexdump -C | grep -A 3 -B 3 MegaTopSecret
And... It found a place in swap, that contained many such strings. That was the tsd
process.

I have tried two times, using different strings, and it worked.

Now imagine, that someone hibernates with some secrets in memory, dehibernates, closes secret-holding applications, shuts the system down, and the swap partition
gets somehow stolen. 

The secrets, together with all process data can be found on that swap. 

That's it. The test program source follows.


```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>
/**
 *The program lets the user put in computer memory some string.
 *The string is passed as program's command line argument.
 *Having put the string in memory, the program waits for any key to be
 *pressed and finishes it's execution. It has been designed for 
 *security investigation needs.
 */

int main(int argc, char**argv){
	if(argc!=2){
		printf("Usage: tsd string_to_put_to_memory\n");
		return 1;
	}
	char* tsd_str=argv[1];
	int N=1000;
	size_t len=strlen(tsd_str);
	char* mem=(char*)malloc(N*(len+1));
	int j;
	for(j=0;j<N;j++){
		strcpy(mem+j*(len+1),tsd_str);
	}
	printf("String %s has been put to memory.\n",mem+500*(len+1));
	printf("Press any key to continue\n");
	getchar();
	return 0;
}

```

---

