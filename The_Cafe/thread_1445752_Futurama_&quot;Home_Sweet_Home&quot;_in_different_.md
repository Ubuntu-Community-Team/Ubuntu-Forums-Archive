---
title: "Futurama &quot;Home Sweet Home&quot; in different programming languages"
date: 2010-04-03
forum: The Cafe
---

### Post by PryGuy on 2010-04-03
Good day, people!

In Futurama's '[I, roommate]("http://en.wikipedia.org/wiki/I,_Roommate")' episode there is a pic on the wall:

[IMG]http://img437.imageshack.us/img437/7439/bscap0001gc.jpg[/IMG]

It resembles Basic I had on my Sinclair ZX-Spectrum, and it should look like:
```
10 PRINT "Home"
20 PRINT "Sweet"
30 GOTO 10
```

In bash it would look like:
```
#!/bin/bash

while [ true ]; do
  echo "Home"
  echo "Sweet"
done
```

Any other programming languages, please... :)

---

### Post by sydbat on 2010-04-03
I miss Futurama...

---

### Post by PryGuy on 2010-04-03
Me too... That's why I started watching it all over again the other day...

---

### Post by sydbat on 2010-04-03
A friend of mine has all 5 seasons on DVD. I should borrow them. What season is 'I, roommate' in?

---

### Post by PryGuy on 2010-04-03
1 season, 3 episode

---

### Post by sydbat on 2010-04-03
Is that the one where Fry stays with Bender for awhile and finds out there is a whole luxurious suite just through a doorway? If so, then I remember it...I'll have to pay closer attention when I borrow the DVD's.

---

### Post by Chronon on 2010-04-03
New episodes are starting June 2010 on Comedy Central!!

---

### Post by chessnerd on 2010-04-03
Java:

```
public class HomeSweetHome {
   public static void main(String[] args) {
      while (true) {
         System.out.println("Home");
         System.out.println("Sweet");
      }
   }
}
```

Futurama is a pretty good show.

---

### Post by aldld on 2010-04-03
Python:

```

while True:
    print 'Home'
    print 'Sweet'

```

---

### Post by PryGuy on 2010-04-03
> **sydbat said:**
> Is that the one where Fry stays with Bender for awhile and finds out there is a whole luxurious suite just through a doorway? If so, then I remember it...I'll have to pay closer attention when I borrow the DVD's.Yep, that's the episode!

---

### Post by prodigy_ on 2010-04-03
DOS/Windows batch:
```
:10
@echo HOME 
@echo SWEET
@goto 10
```

---

### Post by Untitled_No4 on 2010-04-03
PHP:
```

<?php
while (TRUE) {
    echo "HOME\n";
    echo "SWEET\n";
}

```


Edit: forgot one semi-colon.

---

### Post by PryGuy on 2010-04-03
> **Untitled_No4 said:**
> PHP:I've been waiting for that! ;)

---

### Post by clonne4crw on 2010-04-06
x86 (Linux) Assembly language:
```

home db "Home", 0
lenHome db $ - home
sweet db "Sweet", 0
lenSweet db $ - sweet

jmp main

PrintHome:
	mov edx, lenHome
	mov ecx, home
	mov ebx, 1
	mov eax, 4
	int 0x80
	ret

PrintSweet:
	mov edx, lenSweet
	mov ecx, sweet
	mov ebx, 1
	mov eax, 4
	int 0x80
	ret

main:
	call PrintHome
        call PrintSweet
        jmp main
	
        mov eax, 1
	int 0x80

```

---

### Post by SoFl W on 2010-04-06
In one episode they had some sort of scanner, when they scanned Bender it showed he was using a 6502 chip.

---

### Post by dragos240 on 2010-04-06
I wish I knew more C.

---

### Post by chappajar on 2010-04-06
> **dragos240 said:**
> I wish I knew more C.
int main(){
while (1) 
 printf(''HOME\nSWEET\n'');
}

---

### Post by Sporkman on 2010-04-06
[Sporkl:]("http://sporkforge.com/sporkapps/doc/index.php")

```

for (int i=0; i<100000; ++i)
{
   print("Home\nSweet\n");
}
```

I had to cap it at 100000, as it craps out when you print out much more (given that it runs in an online environment)... :)

---

### Post by NovaAesa on 2010-04-06
Scheme:

```

(define (foo)
   (display "home")(newline)
   (display "sweet")(newline)
   (foo))
(foo)

```

EDIT: anyone know if this can be done in scheme with an anonymous procedure?

---

### Post by red_Marvin on 2010-04-06
perl
```
'while(1){print for("home\n","sweet\n")};'
```

forth
```
: home-sweet begin ." home" cr ." sweet" cr again ; home-sweet
```

sed (with echo initialization)
```
echo home|sed -n 'x;s/.*/sweet/;:x;x;p;bx'
```

more mixed bash tools, just because it is fun
```
yes|sed 's/./hom&esw&&t/'|tr ye 'e\n'
```

befunge93 (and probably later versions too)
```
v           ># #<      v
>052*"teews" 52* "emoh"v
            ^,_ ^#:<   <
```
[size=1]EDIT: It is possible to write the perl/sed/befunge examples in much less interesting ways.[/size]

---

### Post by clonne4crw on 2010-04-06
Machine language:
```

A38601002A940000005400000050000000555555550000008247000D000800130080001A000000240000401B2F000040363400030039000340054100034006470003400C6C696E7578486F6D655377656574486F6D65005F7374617274005072696E74486F6D65005072696E745377656574006D61696E00686F6D65006C656E486F6D65007377656574006C656E537765657400204266BA0383050000004266B983000000005166BB0100000066B804000000CD80C366BA830C0000004266B983060000006066BB0100000066B804000000CD80C3E8C7FFE8DFFFE9F7FF66B801000000CD80234D486F6D6500055377656574000600

```

---

### Post by Dr Belka on 2010-04-07
C++

```
#include <iostream>

using namespace std;

int main()
{
    while (1)
    {
        cout << "home" << endl;
        cout << "sweet" << endl;
    }
    return 0;
}
```

---

### Post by schauerlich on 2010-04-07
brainfsck

prints it 5 times, but it could easily be changed to go infinitely many times - just don't decrement the counter cell

```
print out "Home Sweet\n" 5 times

+++++               how many times to loop through
[
  >
  
  +++++ +++++       multiply by 10
  [
    >
    +++++ ++        70 for our capital letters
    >
    +++++ +++++     100 for beginning upper case
    >
    +++++ +++++ ++  120 for end of lower case       
    >
    +++             30 for our space char
    >
    +               10 for our newline
  
    <<<<<           Go back to our counter
    -               decrease it
  ]

  >                 Go to upper case (70)
  ++                72 "H"
  .

  >                 Go to beginning lower case (100)
  +++++ +++++ +     111 "o"
  .
  --                109 "m"
  .
  ----- ---         101 "e"
  .

  >>                Go to control chars (30)
  ++                32 " "
  .

  <<<               Go to upper case (72)
  +++++ +++++ +     83 "S"
  .

  >>                Go to end lower case (120)
  -                 119 "w"
  .
  <                 Go to lower case beginning (101)
  .                 101 "e"
  .                 101 "e"

  >                 Go to lower case end (119)
  ---               116 "t"
  .

  >>                Go to newline (10)
  .                 10 "\n"
  
  clear all variables for next loop
  [-]               newline
  <
  [-]               space
  <
  [-]               end lower
  <     
  [-]               beg lower
  <
  [-]               capital
  
  <<                decrement counter
  -
]
```

---

### Post by Zoot7 on 2010-04-07
Verilog

```
module home_sweet_home;
  initial 
    begin
      $display("Home Sweet Home!");
       #10  $finish;
    end
endmodule
```

---

### Post by Dayofswords on 2010-04-07
REQUEST: 

LOLCODE please =)

---

### Post by Zoot7 on 2010-04-07
> **Dayofswords said:**
> REQUEST: 

LOLCODE please =)

Unless I'm wrong this'll do the job. :)
```
HAI
CAN HAS STDIO?
IM IN YR LOOP
    VISIBLE "HOME SWEET HOME!1!!"
IM OUTTA YR LOOP
KTHXBYE
```

---

### Post by Dayofswords on 2010-04-07
> **Zoot7 said:**
> Unless I'm wrong this'll do the job. :)
```
HAI
CAN HAS STDIO?
IM IN YR LOOP
    VISIBLE "HOME SWEET HOME!1!!"
IM OUTTA YR LOOP
KTHXBYE
```

[IMG]http://www.kitchenroundtable.com/i/smiley/udaman.gif[/IMG]

---

### Post by J V on 2010-04-07
> **Dayofswords said:**
> REQUEST: 

LOLCODE please =)I was just about to say :)

---

### Post by sxmaxchine on 2010-04-07
that is so cool i would never have picked up on that

---

### Post by weichimaster on 2010-04-07
For a proprietary example, VBA outputting into Excel:

```

Option Explicit
Sub home_sweet()
    Dim i As Integer
    i = 1
    Do While (True)
        Cells(i, 1) = "Home"
        Cells(i + 1, 1) = "Sweet"
        i = i + 2
    Loop
End Sub

```

---

### Post by weresheep on 2010-04-07
AWK

```
 awk 'BEGIN {for (;;) {print "Home\nSweet"} }'
```

-weresheep

---

### Post by MarcusW on 2010-04-07
Matlab:

```
while(true)
    fprintf('Home\nSweet\n')
end
```

---

### Post by whiskeylover on 2010-04-07
PLSQL

Note: the output in PLSQL is always single buffered. There is no FLUSH in PLSQL. Everything a program ever outputs is stored in a single buffer and output at the end, or if the buffer overflows, an exception is thrown.

```

SET serveroutput ON
BEGIN
    WHILE 1 = 1
    LOOP
        dbms_output.put_line('HOME');
        dbms_output.put_line('SWEET');
    END LOOP;
EXCEPTION
WHEN OTHERS THEN
    NULL;
END;


```OR
```

DECLARE
    ind_max NUMBER;
    CURSOR cur
    IS
         SELECT id, column1 FROM table1 ORDER BY id, column1;
BEGIN
    ind_max := 100;
    FOR ind IN 1 .. ind_max
    LOOP
         INSERT INTO table1
            (id, column1
            ) VALUES
            (ind, 'HOME'
            );
         INSERT INTO table1
            (id, column1
            ) VALUES
            (ind, 'SWEET'
            );
        COMMIT;
    END LOOP;
    FOR r_cur IN cur
    LOOP
        dbms_output.put_line
        (
            r_cur.column1
        )
        ;
    END LOOP;
EXCEPTION
WHEN OTHERS THEN
    NULL;
END;

```

---

### Post by KdotJ on 2010-04-07
> **Zoot7 said:**
> Unless I'm wrong this'll do the job. :)
```
HAI
CAN HAS STDIO?
IM IN YR LOOP
    VISIBLE "HOME SWEET HOME!1!!"
IM OUTTA YR LOOP
KTHXBYE
```

lol thats awesome stuff

---

### Post by PryGuy on 2010-04-07
> **schauerlich said:**
> brainfsck

prints it 5 times, but it could easily be changed to go infinitely many times - just don't decrement the counter cell

```
print out "Home Sweet\n" 5 times

+++++               how many times to loop through
[
  >
  
  +++++ +++++       multiply by 10
  [
    >
    +++++ ++        70 for our capital letters
    >
    +++++ +++++     100 for beginning upper case
    >
    +++++ +++++ ++  120 for end of lower case       
    >
    +++             30 for our space char
    >
    +               10 for our newline
  
    <<<<<           Go back to our counter
    -               decrease it
  ]

  >                 Go to upper case (70)
  ++                72 "H"
  .

  >                 Go to beginning lower case (100)
  +++++ +++++ +     111 "o"
  .
  --                109 "m"
  .
  ----- ---         101 "e"
  .

  >>                Go to control chars (30)
  ++                32 " "
  .

  <<<               Go to upper case (72)
  +++++ +++++ +     83 "S"
  .

  >>                Go to end lower case (120)
  -                 119 "w"
  .
  <                 Go to lower case beginning (101)
  .                 101 "e"
  .                 101 "e"

  >                 Go to lower case end (119)
  ---               116 "t"
  .

  >>                Go to newline (10)
  .                 10 "\n"
  
  clear all variables for next loop
  [-]               newline
  <
  [-]               space
  <
  [-]               end lower
  <     
  [-]               beg lower
  <
  [-]               capital
  
  <<                decrement counter
  -
]
```Thanks, pal! I've been waiting for the good ole brainfsck! :)

---

