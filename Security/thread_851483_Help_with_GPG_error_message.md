---
title: "Help with GPG error message"
date: 2008-07-06
forum: Security
---

### Post by Bobrm2 on 2008-07-06
I am attempting to create a revoke key, and received the error message posted below. Could someone explain it to me. Thank you

bob@bob-desktop:~$ gpg --output revoke.asc --gen-revoke <KEY-ID>
bash: syntax error near unexpected token `newline'



gpg --output revoke.asc --gen-revoke <KEY-ID>''

Bob

---

### Post by unutbu on 2008-07-06
```

actor@studio:~% <>
bash: syntax error near unexpected token `newline'
actor@studio:~% <
bash: syntax error near unexpected token `newline'
actor@studio:~% >
bash: syntax error near unexpected token `newline'

```

I'm guessing your <KEY-ID> literally includes a < or a >. 
I'm not familiar with the --gen-revoke option, the man page says you are supposed to feed it a name, but it doesn't say what a name is. If a name is the same thing as a KEY-ID, then you are feeding it the right thing. Leave off the < and > around the name (KEY-ID?) if you are including them. 

If the name (KEY-ID?) really does include a < or > symbol, then you can protect them from bash interpretation by putting a backslash in front of them: \< or \>.

---

### Post by Bobrm2 on 2008-07-06
Thank you very much, It is hard enough for me to see the very difficult, let alone the really simple.  Leaving the brackets < > out did the trick.

Bob:)

---

