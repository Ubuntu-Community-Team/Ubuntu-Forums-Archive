---
title: "Python on Windows"
date: 2011-04-05
forum: The Cafe
---

### Post by pi3.1415926535... on 2011-04-05
I am trying to find some way to distribute a Python file that can run on Windows computers without Python. Is there an alternative to py2exe, which seems to be too complicated.

Thank you

---

### Post by GWBouge on 2011-04-05
Not that I have found, but py2exe isn't all that complicated once you get it.  It's been a year or so since I've done it, so this is all from memory, but the process is something like:

Make a simple setup.py file:

```
from distutils.core import setup
import py2exe

setup(
	windows=['my_program.pyw'],
	zipfile=None
)
```

and then call it through the command line with:

```
python setup.py py2exe
```

If I remember right, this will create a 'build' and 'dist' subdirectory.  You can delete the build directory, and what exists in the dist directory is what you distribute ... copy that stuff to the directory that your main script is in, and you should be good to go.  Depending on your program, you may also need to have 'msvcp90.dll' both for compilation and distribution ... just drop it in the main directory of your newly compiled program.

If your program has more than one file in it, just make sure that EVERYTHING that is 'import'ed throughout the program, is imported in the main script, else you'll have dependency issues.  It's also worth noting the '.pyw' extension, which on Windows, will hide the command prompt window that usually shows up on a regular .py (if you didn't know that already).

**EDIT**
Afterthought:  It's good to have a nice, simple main script that calls other things in the program if you plan on updating it often.  For example, if you have a 'modules' subdirectory in your program, your program can access updated .py (or even .pyc) files from that directory without having to redo the py2exe process (so long as you didn't add anything ... if you're importing something new, you'll have to recompile)

---

### Post by Legendary_Bibo on 2011-04-05
Have a secret installation file that installs Python for that person and even changes the registry keys so that Python integrates itself within the shell.

---

### Post by pi3.1415926535... on 2011-04-05
> **Legendary_Bibo said:**
> Have a secret installation file that installs Python for that person and even changes the registry keys so that Python integrates itself within the shell.
:lolflag:
Well, I was thinking that I could distribute it with a link to Portable Python, which is slightly less drastic, and would require less cracking ( or would it be hacking, because they would then have Python on their computer which would be an improvement.:D

Thank you

---

### Post by ukripper on 2011-04-06
> **pi3.1415926535... said:**
> I am trying to find some way to distribute a Python file that can run on Windows computers without Python. Is there an alternative to py2exe, which seems to be too complicated.

Thank you

I normally use CX_freeze(using GUI2EXE) for exe . 

And on client machine just install Microsoft Visual C++ 2008 Redistributable Package and it all works!

More info on GUI2EXE here - [http://www.blog.pythonlibrary.org/2010/08/31/another-gui2exe-tutorial-build-a-binary-series/](http://www.blog.pythonlibrary.org/2010/08/31/another-gui2exe-tutorial-build-a-binary-series/)

---

### Post by undecim on 2011-04-06
> **pi3.1415926535... said:**
> :lolflag:
Well, I was thinking that I could distribute it with a link to Portable Python, which is slightly less drastic, and would require less cracking ( or would it be hacking, because they would then have Python on their computer which would be an improvement.:D

Thank you

Installing a dependency isn't {h,cr}acking.

If you want this to be portable, you can execute Python code in C. [http://www.linuxjournal.com/article/8497](http://www.linuxjournal.com/article/8497)

Just make a small C program wrapper. When compiled, the wrapper will include the python interpreter, and it will run your Python code.

---

