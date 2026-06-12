---
title: "Files created using a software written in a specific programming language"
date: 2016-08-09
forum: The Cafe
---

### Post by tech291083 on 2016-08-09
Hi Friends,

If I write a simple text editing software (just like Gedit etc.) using a particular language such as C and then create a text file using this software only, will this file be written in C as well? Although the file extension will be .txt itself.

And what about different types of files created using other popular software such as MS Word, Excel, PowerPoint, Gimp, HTML editors?

Thanks.

---

### Post by kurja on 2016-08-09
If you write a program that generates a file called something.txt and writes "abc" in it, it will become a file containing the characters abc in it. It's just that and not in any "language". 

What about those different files? You can view (and edit) HTML and Word documents with gedit to see what's in there and what everything does. Stuff that isn't meant to be displayed as a character set, like pictures you'd make with gimp, aren't really readable this way.

---

### Post by grahammechanical on 2016-08-09
HTML editors are text editors. In fact we can create an HTML file using any text editor no matter how limited its functions are. We just need to know the Hyper text markup codes. A HTML editor will allow us to select text and click an icon to enclose the selected text with markup tags but we can insert the tags ourselves if we wish.

An html file and a css file our just text files. They have different markup relative to their purpose and different file types to help the browser know what to do with the file.

You program would have to be smart enough to distinguish characters that are text and characters that are markup. You might want to provide your users with a mode that shows an author how the page would look when rendered by a browser or when printed. Yes, the codes that printers respond to are also a form of markup.

Regards.



Regards.

---

### Post by tech291083 on 2016-08-10
> **kurja said:**
> If you write a program that generates a file called something.txt and writes "abc" in it, it will become a file containing the characters abc in it. It's just that and not in any "language". 


Yes, it get what you mean. Thanks.

---

### Post by tech291083 on 2016-08-10
> **grahammechanical said:**
> 
HTML editors are text editors. In fact we can create an HTML file using any text editor no matter how limited its functions are.
An html file and a css file our just text files. 


Hi grahammechanical,

You are 100% right. I have done some HTML, CSS, C and Java myself, but I was self-taught though. 

I think I understand the fact when you write/create a software in a programming language of your choice, the files created using that software itself can be of different format. As I said earlier, if I create a text editor in C language, then this text editor will create files mainly in .txt format (or a format I intend to have) ie with .txt file extension. Then it is up to the OS to interpret this text file for user. Right?

I also should ask for apology here as I might have misconstrued my original question.  I should rather ask how is it possible that an OS can deal with a variety of software written in so many different languages. What is between (the middle layer/middleman) an OS and a software that makes it possible? Is the API mechanism responsible for this?

[https://en.wikipedia.org/wiki/Application_programming_interface](https://en.wikipedia.org/wiki/Application_programming_interface)

And one more thing, I have heard about digital forensics, probably used by anti-virus companies that do reverse engineering ie unlock the code in which a virus has been written, I hope I am explaining this in the right manner, if not please accept my apology in advance.

So if I were to do this reverse engineering ie unlocking the code using some digital forensics tool on my text file containing some text created using a text editor written C language, will I find some C code as well, since the text editor itself is written is C?[URL="https://en.wikipedia.org/wiki/Application_programming_interface"]
[/URL]
Thanks a lot and regards.

---

### Post by tech291083 on 2016-08-10
I just found that the tools that are used to read ie break the code of a file/virus are called debuggers. Thanks


[https://en.wikipedia.org/wiki/Debugger](https://en.wikipedia.org/wiki/Debugger)

---

### Post by montag dp on 2016-08-10
> **tech291083 said:**
> Hi grahammechanical,

You are 100% right. I have done some HTML, CSS, C and Java myself, but I was self-taught though. 

I think I understand the fact when you write/create a software in a programming language of your choice, the files created using that software itself can be of different format. As I said earlier, if I create a text editor in C language, then this text editor will create files mainly in .txt format (or a format I intend to have) ie with .txt file extension. Then it is up to the OS to interpret this text file for user. Right?

I also should ask for apology here as I might have misconstrued my original question.  I should rather ask how is it possible that an OS can deal with a variety of software written in so many different languages. What is between (the middle layer/middleman) an OS and a software that makes it possible? Is the API mechanism responsible for this? The middleman is either the compiler or interpreter. In compiled languages like C, C++, Fortran, etc., the compiler converts the source code into a binary format that can be executed. In interpreted languages, like Python and Java, a similar process happens, but it occurs on-the-fly. You can read these Wikipedia pages for more information:

[https://en.wikipedia.org/wiki/Compiler](https://en.wikipedia.org/wiki/Compiler)
[https://en.wikipedia.org/wiki/Compiled_language](https://en.wikipedia.org/wiki/Compiled_language)
[https://en.wikipedia.org/wiki/Interpreted_language](https://en.wikipedia.org/wiki/Interpreted_language)

Either way, the OS doesn't know or care what language the program was written in. Programming languages can be thought of as a high-level construct designed to be easy for humans to understand, and the compiler or interpreter translates it into a form that the computer can understand.

> **tech291083 said:**
> [https://en.wikipedia.org/wiki/Application_programming_interface](https://en.wikipedia.org/wiki/Application_programming_interface)
An API is a specification for how a programmer interacts with an existing code or library when creating new code. Let's say you have a software library that performs certain tasks. The API would comprise the function names, inputs, and outputs that the programmer would need to utilize the library in his/her own code. It's completely different from a compiler or interpreter.

> **tech291083 said:**
> And one more thing, I have heard about digital forensics, probably used by anti-virus companies that do reverse engineering ie unlock the code in which a virus has been written, I hope I am explaining this in the right manner, if not please accept my apology in advance.

So if I were to do this reverse engineering ie unlocking the code using some digital forensics tool on my text file containing some text created using a text editor written C language, will I find some C code as well, since the text editor itself is written is C?[URL="https://en.wikipedia.org/wiki/Application_programming_interface"]
[/URL]
Thanks a lot and regards.Your text file is not an executable program, so it's really not relevant. It is merely a way to store data. A virus (or other program) is a set of instructions that perform certain tasks or produce certain output when given some input. There is no way to determine which program created a particular text file, unless it is written in the file itself.

---

### Post by WinEunuchs2Unix on 2016-08-10
The OP won't be writing a text editing program.

C is a tool. .txt is a file format. Interchanging formatted data between applications like excel, databases, etc. is most commonly done with the .csv (comma separated values) format or something similar.

---

### Post by tech291083 on 2016-08-11
> **montag dp said:**
> 
The middleman is either the compiler or interpreter.


Yes, you are right, I know remember reading about them more than a decade in high school.

> 
Programming languages can be thought of as a high-level construct designed to be easy for humans to understand, and the compiler or interpreter translates it into a form that the computer can understand.


You have put it very nicely.


> 
An API is a specification for how a programmer interacts with an existing code or library when creating new code. Let's say you have a software library that performs certain tasks. The API would comprise the function names, inputs, and outputs that the programmer would need to utilize the library in his/her own code. 


This is really useful as I thought an API itself is a piece of code/library capable of performing some pre-defined tasks on its own.

Very nice explanation. Took me all the way back to my high school days. Many thanks and regards.

---

### Post by tech291083 on 2016-08-11
If these anti-virus/data security firms need to look at the code contained in a computer virus to understand how it works, then they use certain tools, and these tools are called debuggers. Right? And only an executable file can be debugged, correct?

Thanks.

---

### Post by illwieckz on 2016-08-11
A debugger is a program to analyze and trace what another program does. So, to be accurate, debuggers debug programs. Being “executable” means two things:

- file format (for example: ELF), a format the computer can read to run “instructions” stored with this specific format. Usually, compilers (for example: GCC for the C language) are used to convert source code to executable format (commonly stored as a binary format).
- file permission, a special flag describing if a file, is allowed to be launched or not. Programs are files too, so they need this flag to be launchable. This flag is file independent, and of course language independent (the tool chmod is commonly used).

Some programs are not compiled but interpreted&#8239;: they are just human-readable file format and another program convert it to computer instruction on the fly (for example: Python for the Python language).

A debugger is a tool to trace and analyze what a program do. A debugger is language specific, like compilers or interpreters are language specific. You need different specific tools to trace and analyze execution of different programs, according to their original language and their final format. For example GDB is a tool to trace and analyze binary programs formerly compiled from C language.

Debuggers do not exactly show “code contained in a computer program”, if the code was compiled, the debugger can show some complex readable representations, but not the exact code that were used before. The debugger only knows the final code, which is made to be readable by a machine and not a human being, by the way, some things can be converted back but you will not get the exact same code (for example you will lose variables names and function names). The program that does this part is not a debugger but a decompiler, of course debuggers commonly have some decompiler function, sometime very simple.

Usually, debuggers rely on some debugging information the compiler write down especially in the final binary executable format (like function and variable name, line number etc.) so if you want to debug your own program, it's very easy, you just have to tell your compiler to write this debug information into the program, and the debugger can tell you what is happening on every line, at every word of your original source file.

Of course, final distributed programs, and especially closed source programs, do not usually embed these extra informations. Of course, virus do not embed debug information because it increases the final file size and help to understand how it works, which is not expected, and that debug information can reveal some personal habit of the developer, which is not wanted by people doing illegal stuff.

So, security firms need debuggers but decompilers too, but they do not use them to read the original source, they use them to help them to guess what the program does, and sometime it's not easy to read.

The opposite tool is called an obfuscator: an obfuscator modify a program in different ways, like adding irrelevant things or converting simple tasks to complex tasks (as do many detours instead of using the straight line) to make debugger and decompiler task harder. Some programs (like Skype) also try to detect they are traced by a debugger and do wrong unexpected things in order to fool the guy who try to understand what the program does or just stop working.

---

### Post by WinEunuchs2Unix on 2016-08-11
Debugging simply means looking at your source code to find a "bug" or coding error. The term originated when a fly flew into a computer (the size of a room in the 1960's) and fried the circuits.

Taking an executable file and generating source code out of it is called a "decompiler" not a "debugger".

---

### Post by tech291083 on 2016-08-13
> **WinEunuchs2Unix said:**
> 
Debugging simply means looking at your source code to find a "bug" or coding error. 


Ok.

> 
Taking an executable file and generating source code out of it is called a "decompiler" not a "debugger".

This is what sees to have confused me, thanks. So anti-virus companies must be using this decompiler to look and analyze the code of a virus, correct?

Thanks & regards,

---

### Post by tech291083 on 2016-08-13
> 
A debugger is a program to analyze and trace what another program does. So, to be accurate, debuggers debug programs. 

Some programs are not compiled but interpreted&#8239;: they are just human-readable file format and another program convert it to computer instruction on the fly (for example: Python for the Python language).

A debugger is a tool to trace and analyze what a program do. A debugger is language specific, like compilers or interpreters are language specific. You need different specific tools to trace and analyze execution of different programs, according to their original language and their final format. For example GDB is a tool to trace and analyze binary programs formerly compiled from C language.

Debuggers do not exactly show &#8220;code contained in a computer program&#8221;, if the code was compiled, the debugger can show some complex readable representations, but not the exact code that were used before. 
The debugger only knows the final code, which is made to be readable by a machine and not a human being, 


This really explains debuggers well. Fantastic stuff indeed.

> 
by the way, some things can be converted back but you will not get the exact same code.... The program that does this part is not a debugger but a decompiler


You really have very good understanding of the decompilation process. 

> 
So, security firms need debuggers but decompilers too, but they do not use them to read the original source, they use them to help them to guess what the program does, and sometime it's not easy to read.


Ok, I now get this.

Dear Friend,

You have given such a fine explanation, I cannot appreciate you enough, only I can say is thank you very much for all the effort you have put in. 

Thanks & regards,

---

