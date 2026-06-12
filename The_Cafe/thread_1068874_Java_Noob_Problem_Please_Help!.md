---
title: "Java Noob Problem Please Help!"
date: 2009-02-13
forum: The Cafe
---

### Post by iampriteshdesai on 2009-02-13
Hi guys!
I have started learning Java. I am still doing the nitty gritty basics.
I started doing this program, where I want to take input from user into an array. However the user has to input the numbers with a single space to differentiate 2 numbers. However with BufferedReader I can get input with only an Enter kety.
Any help?
sample prog:
[HTML]
<b>
import java.io.*;
class sudoku
{
public static void main(String args[]) throws Exception
{

String sudoku[] = new String[3] ;
System.out.println("Enter first 3 numbers:");
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
int i;
for(i=0; i<3; i++)
sudoku[i] = br.readLine();
for(i=0; i<3; i++)
System.out.println(sudoku[i]);
}
}
</b>
[/HTML]


Any way to enter all the numbers without hitting the enter key after evry number?
Also command line wont do

---

### Post by rickyjones on 2009-02-13
> **iampriteshdesai said:**
> Hi guys!
I have started learning Java. I am still doing the nitty gritty basics.
I started doing this program, where I want to take input from user into an array. However the user has to input the numbers with a single space to differentiate 2 numbers. However with BufferedReader I can get input with only an Enter kety.
Any help?
sample prog:
[HTML]
<b>
import java.io.*;
class sudoku
{
public static void main(String args[]) throws Exception
{

String sudoku[] = new String[3] ;
System.out.println("Enter first 3 numbers:");
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
int i;
for(i=0; i<3; i++)
sudoku[i] = br.readLine();
for(i=0; i<3; i++)
System.out.println(sudoku[i]);
}
}
</b>
[/HTML]


Any way to enter all the numbers without hitting the enter key after evry number?
Also command line wont do

How many numbers at once do you want to read in? If you read it in as a String you can then split it up and convert to int which should work.

Thanks,
Richard

---

### Post by iampriteshdesai on 2009-02-13
Actually I want to enter 9 nos. at a time.
Can you please give me the code?
I haven't dont the IO chapters yet, still stuck at the classes thing.
Gosh, Java Input is a big pain in the ****.
Cin was so sweet. I just asked few of my friends for this BufferedReader thing.

---

### Post by rickyjones on 2009-02-13
> **iampriteshdesai said:**
> Actually I want to enter 9 nos. at a time.
Can you please give me the code?
I haven't dont the IO chapters yet, still stuck at the classes thing.
Gosh, Java Input is a big pain in the ****.
Cin was so sweet. I just asked few of my friends for this BufferedReader thing.

Well, here is what I'm doing. I'll give you the snippets of code that you need, just change some things around and it should work.

The actual line that "reads" the input is this:
```
String fn = keyboardScanner.next();
```
I have a System.out.print() on the line above to serve as a prompt.

keyboardScanner is defined in my class as:
```
private Scanner keyboardScanner;
```

Be sure to include the scanner code:
```
import java.util.*;
```


Now you have a String object (fn). With this you can do a few things. 

1. Split your string up into an array of strings based on a character that you specify.
```
String[] fnArray = fn.split(" ");
```

The above code will split your "fn" String up into substrings using the space character as the splitting point.

2. Trim all your string of extra spaces, just in case.
```
fnArray[0] = fnArray[0].trim();
```

In the above code the [0] is the index in the Array of Strings. You'll probably want to create other String entries to make it easier to keep track of things.

3. Finally you want to convert your String of "1" to an int of "1".
```
int x = Integer.parseInt(yourString)
```


That should get you started. :)

Thanks,
Richard

---

