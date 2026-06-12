---
title: "LF vs CRLF"
date: 2007-11-16
forum: The Cafe
---

### Post by jakubdaniel on 2007-11-16
hi, could anyone explain why WIN uses CRLF instead of LF to make a new line? (i mean 0x0D and 0x0A)

well i know that in WIN CR gets back to beginning of the line and LF jump to the following one. Is there anything that this could be used for?

Does it mean that there is something i could not do on LIN that i could on WIN with these chars?
How does linux handle CR?

---

### Post by popch on 2007-11-16
> **jakubdaniel said:**
> 
well i know that in WIN CR gets back to beginning of the line and LF jump to the following one. Is there anything that this could be used for?

There used to be. Those codes were designed for use with teletype terminals. Much unlike a normal typewriter, they moved the printing mechanism to and fro over the width of the page.

The printing mechanism was called the 'carriage'. You 'returned' the carriage to the left hand side of the paper either to start printing at the beginning of a new line or to start overprinting part of the line you had just written.

When you wanted to start printing on a new line, you also had to move the paper forward by one line. That used to be called the 'line feed' or LF. Hence CR+LF.

Overprinting (restarting a line with just CR) was used to write bold (printing the same character several times at the same place), to underline or strike through some text.

You could also use LF without the CR, in which case printing continued on the line below the other one but without changing the horizontal position. Not so many uses for that.

---

### Post by jakubdaniel on 2007-11-16
well thx

so linux would interpret CR as Carriage return too or wouldnt it?
and linux LF interpretation is the same as CRLF

---

