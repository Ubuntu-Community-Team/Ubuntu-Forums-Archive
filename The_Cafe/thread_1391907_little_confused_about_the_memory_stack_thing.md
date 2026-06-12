---
title: "little confused about the memory stack thing"
date: 2010-01-27
forum: The Cafe
---

### Post by nerdy_kid on 2010-01-27
so, im in the process of learning bout memory, cpu registers, all those treats :)  I am, however, stumped on the concept of the stack.  I went and read [this]("http://en.wikipedia.org/wiki/Stack_(data_structure)") and i think that i understood a bunch of it, but still stuck.  So, i have a couple questions:

Is all memory in a stack?
Is a stack purely a 'concept' or a way of looking at the data, or is it really there in RAM?  I got the impression that it was more a way of looking at the memory, but like i said, im confused :confused:

Hope i put this in the right place......please by kind and move it if i didnt :(

Thanks for any replies!

---

### Post by whiskeylover on 2010-01-27
A Stack is a data structure in memory that lets you do operations like push and pop. So, yeah, its a way of "looking at the data". The stack is implemented by a program in memory.

---

### Post by nerdy_kid on 2010-01-27
> **whiskeylover said:**
> A Stack is a data structure in memory that lets you do operations like push and pop. So, yeah, its a way of "looking at the data". The stack is implemented by a program in memory.

thanks, sorry to be a pain, but does that mean all (used) memory can be 'seen' using the stack concept?  So, is there any part of memory that doesnt use a stack?

---

### Post by whiskeylover on 2010-01-27
No. Simply put, a program is allocated memory by the OS. The program can then choose to create anything inside it (including as many stack objects as possible.)

I suggest you pick up a good book on data structures.

---

### Post by Xbehave on 2010-01-27
It is a concept, the hardware section talks about how it's implemented in hardware and then that some chips have a stack implemented in hardware (e.g you send it an electrical signal to put in an item or you send one to get it out and the hw behaves like a stack.

---

### Post by Simian Man on 2010-01-27
A stack is a way of structuring data.  Stacks can be created and used by programmers in source code, but that isn't the same thing as the architecture's concept of the stack.

Each application has a stack that it uses to store local variables (variables that only exist in one function) and other things.  When your program calls a function, that functions arguments and locals get pushed onto the stack, and when it returns, they are popped back off.

Not all memory is a stack.  There is also a global portion for storing globals, constants, and static variables; and an area called the "heap" which is used to store things that are allocated dynamically with malloc or new.  There is also the memory that actually holds the executing program instructions which is called the text segment.

---

### Post by nerdy_kid on 2010-01-27
> **Simian Man said:**
> A stack is a way of structuring data.  Stacks can be created and used by programmers in source code, but that isn't the same thing as the architecture's concept of the stack.

Each application has a stack that it uses to store local variables (variables that only exist in one function) and other things.  When your program calls a function, that functions arguments and locals get pushed onto the stack, and when it returns, they are popped back off.

Not all memory is a stack.  There is also a global portion for storing globals, constants, and static variables; and an area called the "heap" which is used to store things that are allocated dynamically with malloc or new.  There is also the memory that actually holds the executing program instructions which is called the text segment.

ahhh ok thank you very much, this was very helpful :)

---

