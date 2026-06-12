---
title: "Interesting Programming Questions"
date: 2010-09-26
forum: The Cafe
---

### Post by iampriteshdesai on 2010-09-26
I'll be posting some interesting programming questions, try to see if you can solve them :D

I'll be using Java, but you can use any language.


Question:REVO ADDO

The Commanwealth Games(CG) of INDIA prefer comedies to tragedies. Unfortunately,most of the plays are tragedies. 
Therefore the dramatic advisor of CG (Suresh Kalmadi) has decided to transfigure some tragedies into comedies. 
Obviously, this work is very hard because the basic sense of the play must be kept intact, although all the things change to their opposites. 
For example the numbers: if any number appears in the tragedy, it must be converted to its reversed form before being accepted into the comedy play. 


Reversed number is a number written in numerals but the order of digits is reversed. 
The first digit becomes last and vice versa. For example, if the main hero had 1245 trophies in the tragedy, he has 5421 of them now. 
Note that all the leading zeros are omitted. That means if the number ends with a zero, the zero is lost by reversing (e.g. 1200 gives 21). 
Also note that the reversed number never has any trailing zeros. 


CG needs to calculate with reversed numbers. Your task is to add two reversed numbers and output their reversed sum. 
Of course, the result is not unique because any particular number is a reversed form of several numbers (e.g. 21 could be 12, 120 or 1200 before reversing). 
Input:

The input consists of N cases (equal to about 10000). The first line of the input contains only positive integer N. 
Then follow the cases. Each case consists of exactly one line with two positive integers separated by space.
These are the reversed numbers you are to add.Thus we must assume that no zeros were lost by reversing (e.g. assume that the original number was 12). 
Output:

For each case, print exactly one line containing only one integer - the reversed sum of two reversed numbers. 
Omit any leading zeros in the output. 
Sample Input
3
24 1
4358 754
305 794

Sample output:
34
1998
1

---

### Post by iampriteshdesai on 2010-09-26
Question:CHOCOBAR

Jennifer is a teacher in the first year of a primary school. She has gone for a trip with her class today. 
She has taken a packet of chocobar for each child. Unfortunatelly, the sizes of the packets are not the same. 
Jennifer is afraid that each child will want to have the biggest packet of chocobar and this will lead to quarrels or even fights among children. She wants to avoid this. 
Therefore, she has decided to open all the packets, count the chocobar in each packet and move some chocobar from bigger packets to smaller ones so that each packet will contain the same number of chocobar. 
The question is how many chocobar she has to move.

Input specifications: 
The input file consists of several blocks of data. 
Each block starts with the number of chocobar packets N(1<= N <=10000) followed by N integers (each less than 1000) in separate lines, giving the number of chocobar in each packet. 
After the last block of data there is the number -1.

Output specification: 
The output file should contain one line with the smallest number of moves for each block of data. 
One move consists of taking one chocobar from a packet and putting it into another one. 
If it is not possible to have the same number of chocobar in each packet, output the number -1. 

Example- 
Input file: 5
1
1
1
1
6
2
3
4
-1

Output file: 4
-1

---

### Post by iampriteshdesai on 2010-09-26
You: What's the score? Did I miss much? 
Me: It's 2-1 for elAhli and the second half just started. The first half was quite boring. 
You: Who scored first? elAhli or ezZamalek? 
Me: What difference does it make? 
You: Big difference! I can predict the outcome of the match if I knew the order of which goals were scored in the first half. 
Me: What do you mean? 
You: It's 2-1 for elAhli, right? One of three things could have happened: elAhli scored two goals then ezZamalek scored; Or, elAhli scored its first goal, then ezZamalek, then elAhli again; Or, ezZamalek scored first, then elAhli scored its two goals. 
Me: So?!! I still don't understand what difference does that make? It's still 2-1 for elAhli! Why don't you just relax and let us continue watching the game in peace. 
You: You don't understand!! I believe the probability of who'll win depends on the order of how goals were scored. Now I have to predict the outcome for 3 possibilities. 
Me: And what if the score was 3-2? What would you have done then? 
You: I would have to work for 5 different possibilities. No? 
Me: Of course not! The number of possibilities isn't always equal to the sum. 
You: Can you tell me when will it be equal to the sum? 
Me: You're a programmer, why don't you write a program that counts the number of possibilities and compare it to the sum? 
You: I don't have the time, I want to watch the match. Besides, I have nine other problems to worry about. 
Me: I'll give you a hint. The possibilities will be equal to the sum only if one of the teams scored a certain number of goals. 
Input:

Your program will be tested on one or more test cases. Each test case specifies two natural numbers (A and B ) (separated by one or more spaces) representing the score of the first half. 
No team will be able to score more than 10 goals. 
The last line of the input file contains two -1's (which is not part of the test cases.) 
Output:

Format For each test case where the number of possibilities is equal to the sum, print: 
A+B=C 
Where A and B are as above and C is their sum. 
If the number of possibilities is not equal to the sum, replace the '=' sign with '!=' (without the quotes.) 

Example- 
Input:

2 1 
1 0 
-1 -1 
Output:

2+1=3 
1+0=1

---

### Post by Dustin2128 on 2010-09-26
you're missing crucial options. I like python and perl, for instance.

---

### Post by unknownPoster on 2010-09-26
This looks like a cleverly disguised attempt to get us to do his homework for him...

I could be wrong.

---

### Post by iampriteshdesai on 2010-09-26
nope i'm not!
I just found these interesting brain teasers and i thought i'd share it with all

---

