---
title: "quick c question"
date: 2008-06-03
forum: Repositories &amp; Backports
---

### Post by dmm1285 on 2008-06-03
Is there any case where this:

int ch;
    while((ch = getchar()) != '\n')
        putchar(ch);

would act differently then:

int ch = 0;
while(ch != '\n')
    {
        ch = getchar();
        putchar(ch);
    }

---

### Post by jpkotta on 2008-06-03
They act differently when the character read by getchr() is '\n'.

---

### Post by dmm1285 on 2008-06-03
I see what you mean. I understand why that idiom is so used now. I was trying to think of alternate way besides the in line assignment without repeating myself.

---

### Post by Joeb454 on 2008-06-03
I'm not 100% sure (not written C for a while), but would it be [PHP]while (ch != '\0') //basically, NULL

//rest of code[/PHP]

---

