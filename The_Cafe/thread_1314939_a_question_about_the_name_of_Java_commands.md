---
title: "a question about the name of Java commands"
date: 2009-11-04
forum: The Cafe
---

### Post by chriskin on 2009-11-04
certain commands in Java seem too big for no reason 

for example , is there any reason why "System.out.print" is not called just "print"?
:popcorn:

(just started programming on first year at University , the question might be too stupid)

---

### Post by dearingj on 2009-11-04
> **chriskin said:**
> for example , is there any reason why "System.out.print" is not called just "print"?

I wouldn't really call it a "command"; it's a function. A function which is part of the out object, which is part of the System object. You could, if I'm not mistaken (haven't tried this)  create your own object of the same type as out and have your object output to the console, so then you'd only have to call something like

```
myOut.println();
```

Or, probably a simpler thing to do would be to create a print() function in your program, which just calls System.out.println() itself, so you'd only have to call print().

---

### Post by RiceMonster on 2009-11-04
> **dearingj said:**
> It's not really a command as such; it's a function. A function which is part of the out object, which is part of the System object.

I think the word you're looking for is method, not function.

---

### Post by kavon89 on 2009-11-04
> **chriskin said:**
> certain commands in Java seem too big for no reason 

for example , is there any reason why "System.out.print" is not called just "print"?

When it comes down to it, everything in Java is something called a class. System is the class that was designed for things such as printing to a terminal.

Also, there is no such thing as a command in Java. In that statement, what you're actually doing is calling the static method "print()" of the static [PrintStream]("http://java.sun.com/javase/6/docs/api/java/io/PrintStream.html") object "out" within the class [System]("http://java.sun.com/javase/6/docs/api/java/lang/System.html").

---

### Post by dearingj on 2009-11-04
> **RiceMonster said:**
> I think the word you're looking for is method, not function.

Is there a difference? I was always taught that they're two words for the same thing.
[http://en.wikipedia.org/wiki/Function_%28computer_science%29](http://en.wikipedia.org/wiki/Function_%28computer_science%29)

---

### Post by RiceMonster on 2009-11-04
> **dearingj said:**
> Is there a difference? I was always taught that they're two words for the same thing.
[http://en.wikipedia.org/wiki/Function_%28computer_science%29](http://en.wikipedia.org/wiki/Function_%28computer_science%29)

Similar, but not the same. A method is more or less a function within/belonging to a class. A function is independent, not contained within anything.

This would be a function (in C):
```
int addNums(int x, int y) {
    return x + y;
}

```

This would be a method (in C++):
```
class nums {
private:
    int x, y;
public:
   int addNums (int x, int y) {
      return x + y;
   }
}

```

Get what I mean? Sorry for using C/++ rather than Java, I don't really know Java.

---

### Post by dearingj on 2009-11-04
> **RiceMonster said:**
> Similar, but not the same. A method is more or less a function within/belonging to a class. A function is independent, not contained within anything.

<snip>

Get what I mean? Sorry for using C/++ rather than Java, I don't really know Java.

I see :)
I do most of my coding in C++, so no problems understanding your code.

---

### Post by chriskin on 2009-11-04
> **dearingj said:**
> I wouldn't really call it a "command"; it's a function. A function which is part of the out object, which is part of the System object. You could, if I'm not mistaken (haven't tried this)  create your own object of the same type as out and have your object output to the console, so then you'd only have to call something like

```
myOut.println();
```

Or, probably a simpler thing to do would be to create a print() function in your program, which just calls System.out.println() itself, so you'd only have to call print().

what i asked, or at least wanted to ask, was : would there be any problem if the System.out. part was not asked? is it needed or is it just showing that i am using System?

sorry of using the word "command" since everyone commented , it's just that they taught it to us as "entoli" which means command on greek. probably they used the word closer to us from high-school's "programming language"

---

### Post by kavon89 on 2009-11-04
> **chriskin said:**
> what i asked, or at least wanted to ask, was : would there be any problem if the System.out. part was not asked? is it needed or is it just showing that i am using System?


Yes, gigantic problems. Your question is relatively stupid and all you need to know for now is that System.out.print() allows you to print text to a terminal.

---

### Post by chriskin on 2009-11-04
> **kavon89 said:**
> Yes, gigantic problems. Your question is relatively stupid and all you need to know for now is that System.out.print() allows you to print text to a terminal.

i know that my knowledge of Java is too small to even call it basic, but i have seen questions way more stupid than the one i asked.

can you tell me what difference the system.out. part makes and why it is needed?

---

### Post by kavon89 on 2009-11-04
> **RiceMonster said:**
> A method is more or less a function within/belonging to a class. A function is independent, not contained within anything.

Yep, and it's impossible to define a function that does not belong to a class in Java.

---

### Post by kavon89 on 2009-11-04
> **chriskin said:**
> can you tell me what difference the system.out. part makes and why it is needed?

Ugh, ok here goes:

System is an object. It always exists every time you run a Java program and allows you to do things which are related to the computer your program runs on, like asking what time it is.

It also allows you to output text to the computer system's terminal/command line. There is another object that System owns which is called *out*. That object is the compuer system's command line. It has a method [you can think of a method like a command] called print.

In order to access *print*, you must first go to System, then go to *out*. The notation to print to the terminal: Hello World would be as follows:

```
System.out.print("Hello World");
```

If an object called Chef had a "command" called cookDinner, it would look like this:

```
Chef.cookDinner();
```

---

### Post by mehaga on 2009-11-05
> **kavon89]
Your question is relatively stupid
[/QUOTE]
Wow
[QUOTE=kavon89 said:**
> 
System is an object... 
Now, that's stupid.

---

### Post by kavon89 on 2009-11-05
> **vekaz said:**
> Now, that's stupid.

[QUOTE=Java API]public final class System extends Object[/QUOTE]

Every class in Java extends Object and an instance of a class is an object. If chriskin were to be told that System is an object, it isn't completely wrong yet understandable.

---

### Post by hobo14 on 2009-11-05
> **vekaz said:**
> Wow

Now, that's stupid.
?

---

### Post by Hyporeal on 2009-11-05
If you're a fan of brevity, you could use a static import:

```
import static System.out;
```

Then you can write to standard output with:

```
out.println("Hello");
```

This, however, is incorrect:

```
println("Hello"); // INCORRECT
```

You need the "out" because otherwise no one knows what you're writing to. You could have multiple print streams open (files, standard output, standard error, input pipes to other programs, string buffers, etc.) so you need to specify "out" to let the runtime know what you're printing to.

However, I would recommend that you keep the full "System.out.println" because it is so common that people immediately understand what it does. It improves the readability of your code.

---

### Post by forrestcupp on 2009-11-05
> **kavon89 said:**
> Yes, gigantic problems. Your question is relatively stupid and all you need to know for now is that System.out.print() allows you to print text to a terminal.

That's a relatively stupid response.  It's not a stupid question.

I don't know Java, but in C++, you can use a 
```
using namespace std;
```so that you don't have to put an "**std**" on the front of everything in that namespace.  If that ability is built into C++, there is a reason for it, and it's not a stupid question.

I just don't know if Java has an equivalent.  Someday, I'll take the time to learn Java.

Edit:
Hyporeal already beat me with the answer.

---

### Post by mehaga on 2009-11-05
> **hobo14 said:**
> ?

I just wanted to give 'that's stupid' back to him. See his response and you'll know why I think that was 'stupid'.

---

### Post by kavon89 on 2009-11-05
> **vekaz said:**
> I just wanted to give 'that's stupid' back to him. See his response and you'll know why I think that was 'stupid'.

What's stupid is giving a very complicated explanation to a beginner.

---

### Post by chriskin on 2009-11-05
> **Hyporeal said:**
> 
You need the "out" because otherwise no one knows what you're writing to. You could have multiple print streams open (files, standard output, standard error, input pipes to other programs, string buffers, etc.) so you need to specify "out" to let the runtime know what you're printing to.


thanks :)

> **kavon89 said:**
> What's stupid is giving a very complicated explanation to a beginner.

well, if you didn't want to give the explanation, why bother answering? being a beginner doesn't make somebody stupid so that he can't understand something if you explain it in a way that it doesn't require knowledge of programming :)
the way i see it, everybody was a beginner at programming before they started learning (obviously...)

---

### Post by mehaga on 2009-11-05
> **kavon89 said:**
> What's stupid is giving a very complicated explanation to a beginner.

No need to argue. I believe this forum is Ubuntu's strongest feature. One of the reasons it is so good is that it is noob-friendly most of the time. Your comment was not noob-friendly... Anyway, let's leave 'stupid' out of our future posts, ok? 
No pipe of peace smiley, so I'll offer: :popcorn:

---

