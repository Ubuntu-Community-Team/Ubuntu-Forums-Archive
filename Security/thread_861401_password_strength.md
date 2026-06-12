---
title: "password strength"
date: 2008-07-16
forum: Security
---

### Post by cdenley on 2008-07-16
I'm writing a PHP script to measure the strength of a password. Here are some of the checks

-contains letters AND numbers
-contains non-alphanumeric characters
-contains upper and lower case letters
-is not a dictionary word
-password length

Does anyone have any ideas or suggestions for calculating the strength of a password better? Does anyone know where I can find good dictionary files?

Here is part of my code
[PHP]
function GetRating($pass) {
    global $dictionary_path,$wordlist_path;
    $tips=array();
    $rating=0;
    if($pass=="") {
        $rating=-100;
        $tips[]="Don't use an empty password! Are you stupid?";
    }
    if(dict($pass,$dictionary_path)) {
        $tips[]="Your password is too common, and can easily be guessed.";
        $rating-=4;
    }
    if(dict($pass,$wordlist_path)) {
        $tips[]="Your password should not be an actual word.";
        $rating-=4;
    }
    else if(dict(strtolower($pass),$wordlist_path)) {
        $tips[]="Even with uppercase characters, your password should not be an actual word.";
        $rating--;
    }
    if(unique($pass)==1) {
        $tips[]="You should not use a single character repeated.";
        $rating-=6;
    }
    else if(unique($pass)==2) {
        $tips[]="You should use more than two unique characters.";
        $rating-=3;
    }
    else if(unique(strtolower($pass))==1) {
        $tips[]="You should not use a single letter repeated, even with mixed case.";
        $rating-=2;
    }
    else if(unique(strtolower($pass))==2) {
        $tips[]="You should use more than two unique characters, even with mixed case.";
        $rating--;
    }
    if(isseq($pass)) {
        $tips[]="Your password should not be sequential alphabetically or numerically.";
        $rating-=4;
    }
    else if(isseq(strtolower($pass))) {
        $tips[]="Your password should not be alphabetical, even with mixed case.";
        $rating-=2;
    }
    if(isqwert($pass)) {
        $tips[]="Your password should not be sequential on the keyboard.";
        $rating-=3;
    }
    if(!ctype_alpha($pass) && !ctype_digit($pass))
        $rating+=2;
    else        
        $tips[]="Passwords should contain numbers AND letters.";
    if(!ctype_alnum($pass))
        $rating+=2;
    else
        $tips[]="Non-alphanumeric characters make passwords stronger.";
    if($pass!=strtolower($pass) && $pass!=strtoupper($pass))
        $rating++;
    else if(strtolower($pass)!=strtoupper($pass))
        $tips[]="It helps to mix uppercase and lowercase letters.";
    $lenscore=(strlen($pass)-5)/3;
    if($lenscore>4)
        $lenscore=4;
    $rating+=$lenscore;
    if(strlen($pass)<=5)
        $tips[]="Your password should be AT LEAST 6 characters long. The longer, the better.";
    else if(strlen($pass)<=11)
        $tips[]="The longer the password, the better.";
    if($rating<0)
        $rating=0;
    else if($rating>6)
        $rating=6;
    return array("rating"=>$rating,"tips"=>$tips);
}

function isqwert($pass) {
    if(strlen($pass)<2)
        return false;
    $patterns[]="`1234567890-=";
    $patterns[]="~!@#$%^&*()_+";
    $patterns[]="qwertyuiop[]\\";
    $patterns[]="asdfghjkl;'";
    $patterns[]="zxcvbnm,./";
    $patterns[]="QWERTYUIOP{}|";
    $patterns[]="ASDFGHJKL:\"";
    $patterns[]="ZXCVBNM<>?";
    foreach($patterns as $pattern) {
        if(strstr($pattern,$pass) || strstr(strrev($pattern),$pass))
            return true;
    }
    return false;
}

function isseq($pass) {
    if(strlen($pass)<2)
        return false;
    $chars=str_split($pass);
    for($b=1;$b<count($chars);$b++) {
        $a=$b-1;
        if(abs(ord($chars[$a])-ord($chars[$b]))!=1)
            return false;
    }
    return true;
}

function unique($pass) {
    if($pass=="")
        return 0;
    $chars=str_split($pass);
    $found=array();
    foreach($chars as $char){
        if(!in_array($char,$found))
            $found[]=$char;
    }
    return count($found);
}
[/PHP]

---

### Post by Yannick Le Saint kyncani on 2008-07-16
> **cdenley said:**
> Does anyone know where I can find good dictionary files?

apt-cache search wordlist

Look at all the w* packages, like wamerican-huge, wspanish, wfrench, ...

---

### Post by cdenley on 2008-07-16
> **Yannick Le Saint kyncani said:**
> apt-cache search wordlist

Look at all the w* packages, like wamerican-huge, wspanish, wfrench, ...

Good to know, but not exactly optimized for password checking. Almost every word is repeated with an 's. I suppose I can ignore everything with an apostrophe, and make it lowercase.

The dictionary file I'm using now has some weird lines like
!@!@!@
or
|+_)(*&^%$#@!
I guess the dictionary file is the type of file that people trying to crack the password would be using. Do you think this type of file would be better, or an actual word dictionary? If I use a word dictionary, should I only check for lowercase words, or do people use mixed-case dictionaries to crack passwords?

---

### Post by Yannick Le Saint kyncani on 2008-07-16
Well, I have no idea which would be better, but I guess you could also take a look at cracklib and consider using this library. They also use their own password-list it seems.

Cheers.

---

### Post by DaymItzJack on 2008-07-16
You could be anal and compare how close together the letters are in the alphabet/keyboard. Passwords like "qwert" would be bad, or "abcdef" would be bad.

---

### Post by MaleqAlhaq on 2008-07-17
> **cdenley said:**
> 
[...]
I guess the dictionary file is the type of file that people trying to crack the password would be using. Do you think this type of file would be better, or an actual word dictionary? If I use a word dictionary, should I only check for lowercase words, or do people use mixed-case dictionaries to crack passwords?
Hi!

Why don't you search the dictionary without regards to the case. For the password strength, I think, it is unimportant if I take "PaSsWoRd" or "Password" or "password" they're all pretty weak.
If you're awarding "points" for each test, I would not give any points for a 100% match from a dict. or if all chars have the case (all lower or all upper). Then give maybe 50% for mixed case, that is not equal to the one in the dict and 100% for mixed case and not in the dict. or something like that.

just my 0,02€...

Cheers

MA

---

### Post by hyper_ch on 2008-07-17
> **DaymItzJack said:**
> You could be anal and compare how close together the letters are in the alphabet/keyboard. Passwords like "qwert" would be bad, or "abcdef" would be bad.
which varies again on different keyboard layouts.

---

### Post by twisted_steel on 2008-07-17
There is also a PHP interface to [CrackLib]("http://sourceforge.net/projects/cracklib") available from here: [http://pecl.php.net/package/crack](http://pecl.php.net/package/crack).  It might be worth taking a look at [John the Ripper]("http://www.openwall.com/john/") and seeing how it tries to crack passwords.

---

### Post by cdenley on 2008-07-17
I made some improvements. It checks for patterns, now. I also compare the password to my word list after converting it to lower case, deducting only one point instead of two. Does anyone think this is pointless? A case insensitive dictionary attack would take much longer and probably isn't done much. I guess if someone is brute-forcing, though, it would be most efficient to start with dictionary words, then mixed-case words before trying every other string variation.

Instead of reposting my code, I edited my original post.

---

### Post by hyper_ch on 2008-07-17
I'd take the easy rout and random generate them a password which they can't change, only generate a new one ;)

---

### Post by cdenley on 2008-07-17
> **hyper_ch said:**
> I'd take the easy rout and random generate them a password which they can't change, only generate a new one ;)

I was looking for a compromise between security and usability. If users have to remember a long random string of characters, half of them will probably write it on a post-it and leave it on their desk.

---

### Post by Vivaldi Gloria on 2008-07-17
> **cdenley said:**
> I was looking for a compromise between security and usability. If users have to remember a long random string of characters, half of them will probably write it on a post-it and leave it on their desk.

I think gpw (program to generate pronounceable passwords) generates the easiest to remember random passwords.

```
vivaldi@narval:~$ gpw 14 10
tganshrupp
olutakedde
untrinexci
mandenskil
osssswersh
mandinferm
unsissidec
arthantcha
olocediabl
preepadeal
ancyclasco
oussanknon
ffshalizie
ddessmatip
```

---

### Post by TrombaMarina on 2008-07-17
Generated passwords are useful for one-time first logins.  It might be worth while preventing confusing letters in an auto-generated password for the people who don't know how to cut and paste.  E.g., prevent 0 and O (zero, captial o), prevent 1, l, I (one, lower-case L, capital i) and prevent the combination of letters rn (lower-case R plus lower-case N can look like lower-case M).

But it's bad enough trying to keep people from writing down a password they choose, generating them a "strong" one almost guarantees that they will write it down and stick it to their monitor - which is totally insecure.

A cracker would first use tools similar to those that twisted_steel recommended.  These tools do basically the same thing your code does, but they have person years of effort in them already so they should be much richer.

Scoring:
Passwords that can be found in a cracker's dictionary of the most popular 1,000 passwords should all score zero.  Any dictionary word should score near-zero, even if it's followed by a single digit.  Same with keyboard sequences, but the 1K most popular list should include most of them.  Otherwise, score passwords based on how many digits the maximum number of permutations would be.

There are 26 single-case letters, 26 letters of an alternate case, 10 numbers, and 33 miscellaneous symbols on the standard US keyboard.  If you support utf8, people can enter Hebrew, Arabic, Kanji, or any number of other characters, but they generally don't, so I'm not going to consider more than 95 possible characters.  Here are the character sets I considered in my analysis:

26 single-case letters
36 single-case letters and numbers
52 dual-case letters
62 dual-case letters and numbers

I think its rare to see a user willingly use a symbol in a password, but just for the record, there are
69 single-case letters, numbers, and symbols
95 dual-case letters, numbers, and symbols

The number of possible permutations of a password is the size of the character set raised to the power of the length of the password.  Permutations = charsetSize^pwLength.  So I ran the numbers for 6-character and 8-character passwords with different character sets:

Chars         Permutations Score
26^6           308,915,776     9
36^6         2,176,782,336    10
52^6        19,770,609,664    11
62^6        56,800,235,584    11

26^7         8,031,810,176    10
36^7        78,364,164,096    11
52^7     1,028,071,702,528    13
62^7     3,521,614,606,208    13

26^8       208,827,064,576    12
36^8     2,821,109,907,456    13
52^8    53,459,728,531,456    14
62^8   218,340,105,584,896    15

If a cracker has direct access to the encrypted password and it's less than 8 characters long, consider it cracked in an hour or two, no matter how strong it is.  Look up "Rainbow Tables" to see what I mean.

OK, All of that was pretty interesting to me to put together, but it's mostly irrelevant because the easiest way to get into someone's account is to ask them for their user ID and password.  There are scripts for this on the web (to be read by a human to another human, not a computer) that will keep you awake at night.

I strongly recommend:

 - Make your application wait a random amount of time between 1 and 3 seconds to report a failed login - this will slow down brute force attempts.

 - Make your application lock the users account after 5 failed login attempts - this will limit the number of guesses in a brute force attack.

 - If you can avoid giving any kind of feedback, it helps.  E.G.  If you display, "Wrong User ID" then a cracker can try user IDs until that message disappears and know that they have the right user ID.  If you display "account locked" then you know that you have found a real user ID.  Etc.  Even a one-character difference in your response page is all a cracker needs to know.

 - For a highly secure application, you need to give users a one-time pin that they type at the beginning of their real password.  You can generate a little sheet of these things that they carry around and cross one off each time they log in, or you can get them one of those RSA SecurIds with the changing numeric display if you are willing to pay tens of thousands of dollars.  This is the only way to fool all keystroke recorders.

 - If someone will ever have to email a password (for initial account setup) force the user to change their password on their next login.  Any password sent through email is as good as compromised if anyone is interested enough to try to look for it.

 - Remind your users never to share their user ID or password with anyone.  Make it clear that no-one should ever log on as anyone else or share an account.  Remind them that you will never ask for their password, so that there is never any reason they should provide it to anyone.

Good luck!  (I always tend to write too much.  I joke that my blog just might be the most effective cure for insomnia known to man.  Take it as a compliment that I found your question so interesting.)

---

### Post by /etc/init.d/ on 2008-07-18
> **Vivaldi Gloria said:**
> I think gpw (program to generate pronounceable passwords) generates the easiest to remember random passwords.

```
vivaldi@narval:~$ gpw 14 10
tganshrupp
untrinexci
mandenskil
mandinferm
unsissidec
arthantcha
preepadeal
ancyclasco

```
This is the best advice.  Those passwords are easily memorable, and meet the criterium of being pseudo-randomly generated.

You'd need to mix in some capitalisation and ideally a number and symbol to those, but something like that is definitely a good start.

---

### Post by jdavis72 on 2008-08-26
I know this isn't what you were looking for, but I found this site in relation to this topic. The site has a download link for using offline (and checking for bad script). [http://www.passwordmeter.com/]("http://www.passwordmeter.com/"). Just my 2 cents.

Jeremy

---

### Post by cdenley on 2008-08-27
Interesting link. A lot like mine except no dictionaries.
[http://cdenley.yi.org/pwstrength/](http://cdenley.yi.org/pwstrength/)

---

### Post by cdenley on 2008-08-27
At first I was impressed that they had consistent formulas (mine are sort of trial and error), but they don't seem accurate in all situations. For example, the password "a" receives a higher score than "ahfjckdomrodjk". However, it seems to be completely done in javascript, which means the password doesn't need to be sent to the server, which would be a security benefit. You couldn't properly evaluate a password's strength without a password dictionary, though, and that would make one big javascript file for the user to download. I suppose I could have the dictionary split, then use javascript to grab the appropriate section based on the given password. Maybe I'll try that some time.

---

