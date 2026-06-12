---
title: "java i/o sheevaplug?"
date: 2011-02-19
forum: Server Platforms
---

### Post by Quickmarch on 2011-02-19
Hi there, I can't seem to be able to save a file properly with java on the sheevaplug (ubuntu)

Here's my test-code:
```

try {
            File f = new File("test.txt");
            
            System.out.println(f.exists());
            
            f.createNewFile();
            
            FileWriter write = new FileWriter(f);
            write.write("hello world");
            write.close();
        } catch (IOException e) {
            e.printStackTrace();
        }

```it seems to save the file, but nothing that is readable in ubuntu.

I'm using the openjdk-6-jre package by the way.

Any help appreciated. Thanks.

EDIT: NVM! Forgot to cd into the directory holding the jar before running, so it was working but it was saving to the $HOME dir...

---

### Post by lykeion on 2011-02-20
Your code looks okay, so the problem is probably something else.
When you say it seems to save a file but not something readable in Ubuntu, what do you mean?

First thing I thought of was a character encoding issue. When you use FileWriter it writes in the system's default character encoding. 
You could try use OutputStreamWriter and set character encoding explicitly, something like this:
[PHP]try {
    Writer out = new OutputStreamWriter(new FileOutputStream("test.txt"), "UTF-8");
    out.write("hello world");
    out.close();
} catch (IOException e) {
    e.printStackTrace();
}[/PHP]

Secondly it could be some kind of write permission issue. I've no experience with SheevaPlug. What kind of storage does it have - flash card or an external SATA drive? Do you have a home directory?

---

