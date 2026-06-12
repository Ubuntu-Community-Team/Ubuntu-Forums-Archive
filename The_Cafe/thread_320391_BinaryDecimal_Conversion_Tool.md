---
title: "Binary/Decimal Conversion Tool"
date: 2006-12-17
forum: The Cafe
---

### Post by Verminox on 2006-12-17
I searched all over google but only found converters between Binary/Decimal/Hexadecimal for integral values.

I want to see how floating point numbers are represented in those bases (at least binary, if not hexadecimal). Is there any online tool or software or even simpler a way to break up the "float" and "double" data types in C to show their bit-by-bit value?

---

### Post by maxamillion on 2006-12-17
That is actually going to be a platform specific question but it is my understanding that x86, x86_64 and powerpc all use the same IEEE standard [http://en.wikipedia.org/wiki/IEEE_754](http://en.wikipedia.org/wiki/IEEE_754)

Not sure about a tool that is able to convert this, I assume one could be easily written with the understanding of the method of representation though.

---

### Post by Verminox on 2006-12-17
Yup I guess I could do it manually by understanding the method involved, but I'd rather have a tool to do this automatically.... if I can't find one I'll just use the method stated there and make a program out of it in C++ or something.

---

### Post by Lord Illidan on 2006-12-17
> **Verminox said:**
> I searched all over google but only found converters between Binary/Decimal/Hexadecimal for integral values.

I want to see how floating point numbers are represented in those bases (at least binary, if not hexadecimal). Is there any online tool or software or even simpler a way to break up the "float" and "double" data types in C to show their bit-by-bit value?

Qalculate can do it. It is in the repos.

---

### Post by Verminox on 2006-12-17
Wow. Qalculate has got to be the best calculator I've used yet.... thanks!

---

### Post by patrick295767 on 2006-12-18
> **Verminox said:**
> I searched all over google but only found converters between Binary/Decimal/Hexadecimal for integral values.

I want to see how floating point numbers are represented in those bases (at least binary, if not hexadecimal). Is there any online tool or software or even simpler a way to break up the "float" and "double" data types in C to show their bit-by-bit value?

the very powerful x48 
my howto now there :
[http://www.ubuntuforums.org/showthread.php?t=156767&highlight=x48](http://www.ubuntuforums.org/showthread.php?t=156767&highlight=x48)

---

### Post by Lord Illidan on 2006-12-18
> **Verminox said:**
> Wow. Qalculate has got to be the best calculator I've used yet.... thanks!
U're welcome, I love it too!

---

