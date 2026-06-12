---
title: "This C++ Program makes no sense, maybe I'm stupid."
date: 2006-03-17
forum: The Cafe
---

### Post by ATiGuy on 2006-03-17
I don't get it. Don't the lines accumulator = 0; and while (accumulator != 0); contradict themselves? I don't see how the program exits after I enter in a negative number the second time. I understand how it repeats the loop, but I don't see how it ever gets out of it. Why does enteiring a negative number twice remove it from the loop completely? When entering it only once only restarts the loop? I don't see how the code ever gets to cout << "The total for this sequence is " This is my first time ever with C++ or any real language for the matter.

```

#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

int main(int nNumberofArgs, char* pszArgs[])
{
    // the outer loop
    cout << "This program sums multiple series\n"
         << "of numbers. Terminate each sequence\n"
         << "by entering a negative number.\n"
         << "Terminate the series by entering two\n"
         << "negative numbers in a row\n";

    // continue to accumulate sequences
    int accumulator;
    do
    {
        // start entering the next sequence
        // of numbers
        accumulator = 0;
        cout << "Start the next sequence\n";
 
        // loop forever
        for(;;)
        {
            // fetch another number
            int value = 0;
            cout << "Enter next number: ";
            cin  >> value;

            // if it's negative...
            if (value < 0)
            {
                // ...then exit
                break;
            }

            // ...otherwise add the number to the
            // accumulator
            accumulator = accumulator + value;
        }

        // output the accumulated result...
        cout << "The total for this sequence is " 
            << accumulator 
            << endl << endl;

        // ...and start over with a new sequence
        // if the accumulated sequence was not zero
    } while (accumulator != 0);
    
    // we're about to quit
    cout << "Thank you" << endl;

    // wait until user is ready before terminating program
    // to allow the user to see the program results
    system("PAUSE");
    return 0; 
}
```

---

### Post by GeneralZod on 2006-03-17
If you enter a negative number, then it is not added to the accumulator.  The accumulator is set to 0 before a sequence begins.  Therefore, if the first number you enter for a sequence is negative, the for ( ; ; ) loop exits with the accumulator still equal to 0.  "Entering a negative number twice in a row" counts as ending a sequence (the first negative number you enter) and then entering a negative number for the first element in the next new sequence (the second negative number you enter).

Hope this is reasonably clear! :)

---

### Post by Jucato on 2006-03-17
But if you enter a negative number, won't the for loop just repeat continuously? Isn't a *break* statement supposed to break out of the current loop *and* repeat the loop (without checking the condition)?

So for example, I enter -4 on the first iteration of the for loop, value will be < 0, accumlator will still be = 0. Then because of the break, the cout won't execute, and for loop is started again, and value will be = 0 again. 

If I enter another negative on the second round, the break will again take me back to the start of the for loop, right? So the condition of the do-while will never be checked.

---

### Post by hod139 on 2006-03-17
[quote=ATiGuy]I don't see how the code ever gets to cout << "The total for this sequence is " [/quote] 
This code block here is how it gets to cout << "The total for this sequence is "
```

// if it's negative...
if (value < 0)
{
     // ...then exit
     break;
}

``` 
The break keyword will "break" out of the loop and continue, not restart. 

Hope that helps.

Edit: Missed your post.  You are confusing the continue keyword with break.  Continue will go back to the top of the loop, break will break out of the loop and execute the code immediately following it.

---

### Post by Jucato on 2006-03-17
Ok, I had break and continue mixed up again... :D sorry for that...

Hmm... if you enter a negative value on the first loop, won't it exit immediately (without entering a second negative value?)

---

