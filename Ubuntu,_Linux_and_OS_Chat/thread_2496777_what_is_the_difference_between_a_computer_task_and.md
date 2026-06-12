---
title: "what is the difference between a computer task and an input output task?"
date: 2024-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by howtolinux on 2024-04-12
hey quick question,


what is the difference between a computer task and an input output task?


[https://en.wikipedia.org/wiki/Task_(computing)](https://en.wikipedia.org/wiki/Task_(computing))


is there any difference at all?


thank you

---

### Post by ActionParsnip on 2024-04-12
Sounds like homework to me

---

### Post by TheFu on 2024-04-12
I've never heard of an "input output task".  I wouldn't use those terms together.  Sounds like something a non-native English speaker might use, so I'd have to ask for more specifics, should I wish to help.


Wikipedia seems clear to me.  

"Task" isn't exact enough a term to know what is meant.  I use "task" when speaking with non-computer people.  

I use "process" or "LWP" with computer nerds when threading isn't involved.  MSFT doesn't support LWP due to all the overhead involved in spawning a process. But Unix-like OSes are very much lighter and a small process doesn't have much overhead.  

I use "thread" specifically when I'm doing multi-threaded processing or programming. There are complexities involved in writing multi-threaded programs that are easily missed leading to buggy programs.

For a long time, creating multi-threaded programs on Unix wasn't necessary because we could use multiple processes instead of adding the complexity of MT programming.  Semaphores and judicious file locking could get around having multiple processes trying to use/modify the same resources. It was simple and works with little chances for total locked situations that can be caused using MT programming. Or worse, having the wrong input data used by the wrong thread, which doesn't have homogeneity with all the other input data on a thread.  Using mixed data from different threads is problematic. Race conditions and bad outputs are much more likely leading to all sorts of unexpected data situations.

---

### Post by #&amp;thj^% on 2024-04-12
A couple of years ago I had and wanted to write about, what I think you are asking about, and in a nutshell it read like this:

 A computer works by combining input, storage, processing, and output. All the main parts of a computer system are involved in one of these four processes.

Breif sumary:
[list]
[*]Input: Your keyboard and mouse, for example, are just input units&#8212;ways of getting information into your computer that it can process. If you use a microphone and voice recognition software, that's another form of input.

[*]Memory/storage: Your computer probably stores all your documents and files on a hard drive: a huge magnetic memory. But smaller, computer-based devices like digital cameras and cellphones use other kinds of storage such as flash memory cards.

[*]Processing: Your computer's processor (sometimes known as the central processing unit) is a microchip buried deep inside. It works amazingly hard and gets incredibly hot in the process. That's why your computer has a little fan blowing away&#8212;to stop its brain from overheating! LOL

[*]Output: Your computer probably has an LCD screen capable of displaying high-resolution (very detailed) graphics, and probably also stereo loudspeakers. You may have an inkjet printer on your desk too to make a more permanent form of output. [/list]
More of the same found here: [https://www.computerhope.com/issues/ch001355.htm](https://www.computerhope.com/issues/ch001355.htm)

Also I agree "The term Task is ambiguous"

---

### Post by howtolinux on 2024-04-13
i asked chatgpt and it just gives me it's usual word salad

In the context of computing or programming, a "task" typically refers to a unit of work that needs to be completed by a computer program or system. This could encompass a wide range of activities, such as processing data, performing calculations, handling user interactions, or executing specific instructions.

On the other hand, an "input-output task" specifically refers to tasks that involve taking input from some source (such as a user, a file, or another system), processing that input in some way, and then producing output. Input-output tasks are fundamental in many areas of computing, especially in applications where interaction with users or external systems is involved.

So, while all input-output tasks are tasks, not all tasks necessarily involve input and output operations. The distinction lies in the focus on input and output specifically in input-output tasks.

I/O (Input/Output) refers to the interaction of a computer or computer program with the system's disk and network. Examples of I/O activities include reading/writing data from/to disk, performing HTTP requests, and interacting with databases. These activities are slower compared to accessing RAM or performing computations on the CPU.

what is an example of a task that isn't an i/o task?
ChatGPT
Certainly! Here's an example of a task that isn't an I/O task:

Computational Task: Suppose you have a program that calculates the factorial of a given number. When a user inputs a number, the program performs a series of mathematical operations (multiplications) to compute the factorial. This process involves pure computation without any input/output operations. The task here is purely computational, as it involves performing mathematical operations on data in memory without interacting with external sources such as files or networks.

what is an example of an i/o task?
ChatGPT
An example of an I/O task is reading data from a file. Here's how it might work:


Suppose you have a program that needs to read a list of names from a text file. The I/O task involves opening the file, reading its contents, and then storing the data in memory for further processing.

---

### Post by hyperlinxe on 2024-04-14
They didn't move this thread even though it's not a help request for using ubuntu, because they are just liars...

*Shrug* 

That's the nature of Ubuntu's administrators currently!

---

### Post by QIII on 2024-04-14
Thank you for pointing out the oversight.  Given your many misplaced threads, it happens.

Moved to ULOSC.

---

