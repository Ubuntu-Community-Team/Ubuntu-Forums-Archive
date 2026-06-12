---
title: "windows jdk is installed but the compiler says it isn't"
date: 2008-02-09
forum: Windows
---

### Post by linux noooob on 2008-02-09
like the title says jdk is installed but all my compilers for different .java apps say jdk isn't installed and javac isn't a known internal or external command.

---

### Post by LaRoza on 2008-02-09
What is the result of:

```

echo %path%

```

---

### Post by linux noooob on 2008-02-09
so how would i fix this?

---

### Post by LaRoza on 2008-02-09
> **linux noooob said:**
> so how would i fix this?

What is the output of that command? (The point of giving it in the first place)

If the path to javac isn't there, it would have to be added.

---

### Post by linux noooob on 2008-02-09
thats the problem i can't find the path to javac or anything that has to do with jdk i look through C:\program files\sun\javaDB\ but i find nothing just a lot of documentation.

---

### Post by LaRoza on 2008-02-09
> **linux noooob said:**
> thats the problem i can't find the path to javac or anything that has to do with jdk i look through C:\program files\sun\javaDB\ but i find nothing just a lot of documentation.

Why didn't you post the output of that command?

It will be in 

C:\Program Files\Java\jdk1.6.0_10\bin

---

### Post by linux noooob on 2008-02-09
There isn't any code it is just 

"no jdk 5.0 or 6.0 or updates have been installed. This application requires jdk 5.0 or 6.0 please go to .....some link.... to learn how to install it"

press any key to continue...

(then the window closes)

---

### Post by LaRoza on 2008-02-09
> **linux noooob said:**
> There isn't any code it is just 

"no jdk 5.0 or 6.0 or updates have been installed. This application requires jdk 5.0 or 6.0 please go to .....some link.... to learn how to install it"

press any key to continue...

(then the window closes)

What gives that message?

Open the command prompt: type:

```

echo %PATH%

```

Copy the output and post it here.

Now, go to:

```

C:\Program Files\Java\jdk*****\bin

```

(The versions of jdk will be different, look for it)

There should be many things in that directory, including "javac.exe"

If it is there (it should be if you installed the JDK), add the path to it to your path variable.

---

### Post by linux noooob on 2008-02-09
nvm i fixed the compiler to connect to the javac.exe but now this:

> client.java:5147: unreachable statement
if(item == 4708 && playerLevel[13] >= 85)
^
Note: stream.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
1 error
The system cannot find the path specified.
Press any key to continue . . .

---

### Post by linux noooob on 2008-02-09
doesn't make sense the code > 

if(item == 4708 && playerLevel[13] >= 85)

^ is right there in the client.java file and right were it should be:confused:

---

### Post by LaRoza on 2008-02-09
> **linux noooob said:**
> doesn't make sense the code  is right there in the client.java file and right were it should be:confused:

You are not following my requests....

Every single post of mine asks you to do one simple thing, and you didn't do it.

If you are getting compile errors, then it is installed.

---

### Post by linux noooob on 2008-02-12
Nvm i fixed it i am using a differnet source now and i edited the path to were the javac file is, everything works now

---

