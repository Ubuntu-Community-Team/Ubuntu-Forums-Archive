---
title: "Simple Linux driver, unexpected multiple call of copy_from_user"
date: 2012-09-13
forum: Ubuntu Application Development
---

### Post by nedsana on 2012-09-13
Hi all, 

Recently I got interested in Linux drivers and how they are developed. I am complete beginner in this area, although I am pretty familiar with C language and programming in general.

I tried to create my first driver - a simple one, should be able to store data from user space in some memory and then should be able to read it in user space.

I did some coding, the device is installed as a module, and is operational(I see my printk() dumps). But I face a strange behavior of my file write function. This is what my function looks like(really simple):

ssize_t memory_write( struct file *filp, char *buf,                       size_t count, loff_t *f_pos) 
{   
static int cnt = 0;
  cnt++;
  copy_from_user(memory_buffer,buf,count);
  
  printk(... cnt); 
  printk(... buf);
  printk(... buffer);
  printk(... count);
  return 1; 
}

So what it should do: copy the input string "buf", with length count in a memory_buffer. 

This is how I call it: echo -n 12345 > /dev/my_driver 

But what I see is that this function seems to be called multiple times(count times to be more exact) and each time it reads one character from the input string 12345.

Is this how it should be? If so how can I avoid the multiple call?

I use as reference different web pages, manuals I found there, and Linux Driver Development edition 3. But there I could not find explanation for this(or I missed it).

Any ideas?

Greetings.

---

### Post by nedsana on 2012-09-13
Aham, 
I seem to have asked a really stupid question. 

It is perfectly normal behavior since it is char driver. It is byte oriented and will process the data byte by byte.

---

