---
title: "Simple math question"
date: 2008-08-20
forum: The Cafe
---

### Post by billgoldberg on 2008-08-20
I'm following an online course to learning "ruby" and there are some examples I'm trying out now.

One is "how many seconds old are you".

I'm almost 22 and I used this for it

((((((365*24) * 8 ) + ((366*24)*2)) * 60) * 2) + (((((365*24) * 8 ) + ((366*24)*2)) * 60) / 5)) *60

The outcome being

rw@legend:~$ ruby /home/rw/Documents/rubytest.rb

694172160

Is this correct?

*(note that this is only being done using the "puts" prefix, I'm still in the very beginning of the tutorial)*

The second "harder one" asked how old you are when you are 1011 million seconds old.

I used this

((1011000000/360)/60)/365

than adds to "128".

Also correct?

---

### Post by squaregoldfish on 2008-08-20
Use Google's conversion tool. Just search for:

```
22 years in seconds
```

And you'll have your answer.

Steve.

---

### Post by kirsis on 2008-08-20
1) Not sure how you came up with this formula but it seems you've tried accounting for the leap years too.

Assuming you're exactly 22 and 5 leap years in the 22 year period, what about

(5*366 + 17*365) days = 1830 + 6205 = 8035 days

8035 days * 24 =>
192840 hours * 3600 =>
694224000

Google claims 694 252 371 seconds ([http://www.google.lv/search?q=22+years+in+seconds&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.lv/search?q=22+years+in+seconds&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a))

I wonder how google gets its result, which differs from this by ~7h worth of seconds

[i]edit: from wikipedia: An average Gregorian year is 365.2425 days = 52.1775 weeks, 8,765.82 hours = 525,949.2 minutes = 31,556,952 seconds (mean solar, not SI).

Google uses 31556952 secs per year[/i]

2) The 360 should be 3600 (60 secs * 60 min) and the 60 should be 24

   1011 000 000 secs / 60 =>
   16 850 000 min / 60 =>
   280833,(3) h / 24 =>
   11701,3(8) days / 365 => 
   ~32,06

(this is not counting leap years)

Google says 32,03

[http://www.google.lv/search?hl=lv&client=firefox-a&rls=org.mozilla%3Aen-GB%3Aofficial&hs=vP5&q=1011000000+seconds+in+years&btnG=Mekl%C4%93t&meta=](http://www.google.lv/search?hl=lv&client=firefox-a&rls=org.mozilla%3Aen-GB%3Aofficial&hs=vP5&q=1011000000+seconds+in+years&btnG=Mekl%C4%93t&meta=)

---

### Post by ssam on 2008-08-20
i dont know ruby, but most programming languages let you access the UNIX time stamp (have a look for a date library).

the unix time stamp is in seconds since the start of 1970. there should be functions to easy convert this into a calendar date, and back. This will account for all leap years and leap seconds.

you may consider this cheating from a maths point of view, but you'll learn some other useful stuff. you can compare it to the maths answer.

---

### Post by jespdj on 2008-08-20
No need for difficult calculations. Try this (ssam's idea):
[PHP]birth = Time.local(1971, 8, 9, 17, 55, 0)
now = Time.now

secs = now.to_i - birth.to_i

puts "You are #{secs} seconds old"
[/PHP]
Replace with your own birth date, ofcourse.

---

### Post by billgoldberg on 2008-08-20
> **jespdj said:**
> No need for difficult calculations. Try this:
[PHP]birth = Time.local(1971, 8, 9, 17, 55, 0)
now = Time.now

secs = now.to_i - birth.to_i

puts "You are #{secs} seconds old"
[/PHP]
Replace with your own birth date, ofcourse.

Thanks, but it's the first program language I'm learning (besides xhtml and css, but that doesn't really count) so I don't know 100% what this does (the first two lines).

I do have a question, when I used this:

```


puts 'hello what\'s your name?'
name = gets.chomp
puts 'Ok, ' + name + '. How old are you?'
age = gets.chomp
puts 'You\'re name is ' + name + ' and you\'re ' + age
days = age.to_i * 365
puts 'you\'re ' + days + ' days old'


```

```
I get this error
rw@legend:~$ ruby /home/rw/Documents/rubytest.rb
hello what's your name?
rw
Ok, rw. How old are you?
21
You're name is rw and you're 21
/home/rw/Documents/rubytest.rb:7:in `+': can't convert Fixnum into String (TypeError)
        from /home/rw/Documents/rubytest.rb:7
```

Why?

Or isn't it possible to use "gets" like that?

---

### Post by jespdj on 2008-08-20
[PHP]birth = Time.local(1971, 8, 9, 17, 55, 0)
now = Time.now[/PHP]

This creates two Time objects: one set to 09-08-1971, 17:55 (my birth date... :) ) and one to the current date and time. "Time" is a class in Ruby's standard library (you can look up the documentation for it on [http://ruby-doc.org/core/](http://ruby-doc.org/core/) or in a Ruby reference book).

It then calls to_i on both objects, which converts the date and time represented by those objects into a number of seconds since the UNIX epoch (01-01-1970, 12:00 AM). Substract those two numbers, and you have the number of seconds between the two dates.

About your error, try this:

[PHP]puts 'you\'re ' + days.to_s + ' days old'[/PHP]

You have to explicitly convert days to a string by calling to_s on it. (I don't know exactly why Ruby requires that in this case). You could also write it like this:

[PHP]puts "you're #{days} days old"[/PHP]

Note: There's also a [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) forum, this question really belongs there.

---

### Post by lordhaworth on 2008-08-20
I think it is right, although this version isnt very accurate I did a similar thing when i started learning VBA and for DOB of 01/09/1986 I get number of seconds alive as: 693272600 which is to the same order of magnitude as your answer. 

You gotta remember that seconds isnt very useful, because it can only be "so" accurate. I dont know what second I was born on and dont incorporate the second of the day in **this** calculation. This could allow an error of a maximum of just under 2 days worth of seconds i.e. error < (60 * 60 * 48)
error < 172800

but in a 9s.f. value this makes the accuracy pretty stupid. You can only really get as good as days alive.

I do think yours is about right tho

Tom

---

### Post by sujoy on 2008-08-20
> **billgoldberg said:**
> Thanks, but it's the first program language I'm learning (besides xhtml and css, but that doesn't really count) so I don't know 100% what this does (the first two lines).

I do have a question, when I used this:

```


puts 'hello what\'s your name?'
name = gets.chomp
puts 'Ok, ' + name + '. How old are you?'
age = gets.chomp
puts 'You\'re name is ' + name + ' and you\'re ' + age
days = age.to_i * 365
puts 'you\'re ' + days + ' days old'


```

```
I get this error
rw@legend:~$ ruby /home/rw/Documents/rubytest.rb
hello what's your name?
rw
Ok, rw. How old are you?
21
You're name is rw and you're 21
/home/rw/Documents/rubytest.rb:7:in `+': can't convert Fixnum into String (TypeError)
        from /home/rw/Documents/rubytest.rb:7
```

Why?

Or isn't it possible to use "gets" like that?



you need to change this line 
```
puts 'you\'re ' + days + ' days old'
```
to
```
puts 'you\'re ' + days.to_s + ' days old'
```

because days is a number as was indicated in the error (Fixnum) and hence you cannot apply string concatenation on it.

---

### Post by billgoldberg on 2008-08-20
> **sujoy said:**
> you need to change this line 
```
puts 'you\'re ' + days + ' days old'
```
to
```
puts 'you\'re ' + days.to_s + ' days old'
```

because days is a number as was indicated in the error (Fixnum) and hence you cannot apply string concatenation on it.


It makes sense that you can't add a number to a string.

---

### Post by cpetercarter on 2008-08-20
Trouble is, once you've figured all this out, you're older!

---

