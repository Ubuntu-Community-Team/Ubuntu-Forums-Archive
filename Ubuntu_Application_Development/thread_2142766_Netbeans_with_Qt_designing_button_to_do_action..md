---
title: "Netbeans with Qt designing button to do action."
date: 2013-05-06
forum: Ubuntu Application Development
---

### Post by Bresser on 2013-05-06
Ok so what I am making is a program that converts a message into gibberish using:
```

std::string str;
cin >> str;
int index=0;
while(str[index])
{
str[index]=(str[index]+1)%256;
index++;
}
std::cout << str;

```
But this poses two questions:

1. with cin it doesn't allow for spaces. What can I use that does?
2. how would I convert it back to the message you type in

---

