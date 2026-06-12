---
title: "Hi im back- too many threads have crammed mine down"
date: 2008-07-12
forum: The Cafe
---

### Post by Markissocoollike on 2008-07-12
Hi, I'm a new user to Ubuntu and I'm having problems, scratch my other questions as I am now thinking of just basically reprogramming the GUI (gooie ewwie! ^^) After becomming insane from the constant cannot recognise command or "not found" in the terminal I've decided to turn towards others in this forum I apologize for any rudeness (whatever!) Anyhow...

I'm trying to install ruby (the irony!) here's what i've just done with the terminal:

```
 sudo aptitude install build-essential
Then I typed clear ^^
cd Desktop/
ls
Then it gave me this:
ruby  ruby_1.8.5_2006-08-25.zip  ruby-1.9.0-0  wine-dlls-0.9.14-mingw.zip
(I tried installing 1.9.0-0 with no succession so I then tried 1.8.5)
sudo tar -xvzf ruby-1.8.5-p12.tar.gz --directory=/usr/local/src
and here's what I got :(
tar: ruby-1.8.5-p12.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

Hopefully someone will help me with this please -.-

in the meantime how do I disable the stupid password security it is getting on my nerves (i've been entering it over and over again for every installation I attempt!)

---

### Post by Bachstelze on 2008-07-12
Is there a reason why you want to compile Ruby from source instead of installing it from the repos? See here for more information about installing software in Ubuntu:

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by AnLGP on 2008-07-12
Ruby is in synaptic.

you can sudo synaptic in the terminal or you can find it via the menu System - Administration - Synaptic

then just do a search for the version of ruby you're looking to install.

I don't know if it's possible to remove sudo in Ubuntu.

---

### Post by Markissocoollike on 2008-07-12
> **AnLGP said:**
> Ruby is in synaptic.

you can sudo synaptic in the terminal or you can find it via the menu System - Administration - Synaptic

then just do a search for the version of ruby you're looking to install.

I don't know if it's possible to remove sudo in Ubuntu.

Wow so many rubies 0.o should I check libdbm-ruby1.9? I'm so confused because of all the rubies gosh! :lolflag:

---

### Post by Markissocoollike on 2008-07-12
I've installed it but no program what the hell?

---

### Post by Markissocoollike on 2008-07-12
5 hand grenades standing on a wall,
5 hand grenades standing on a wall,
and if one hand grenade should accidentally fall,
there would be no hand grenades no stupid wall :)

---

### Post by kansasnoob on 2008-07-12
[ATTACH]77498[/ATTACH]

[http://www.trug.ca/Ruby_GUI_Toolkits](http://www.trug.ca/Ruby_GUI_Toolkits)

---

### Post by issih on 2008-07-12
Probably just hasn't created a launcher, open a terminal and type rub then hit tab a couple of times to see what programs start with rub, then view their man pages to work out what you want.

Alternatively reopen synaptic and locate the package you installed. select it and view the properties, in their is a list of the files it installed.

---

### Post by kool_kat_os on 2008-07-12
> **issih said:**
> Probably just hasn't created a launcher, open a terminal and type rub then hit tab a couple of times to see what programs start with rub, then view their man pages to work out what you want.

Alternatively reopen synaptic and locate the package you installed. select it and view the properties, in their is a list of the files it installed.

you mean just type "ruby" ;-)

---

### Post by Markissocoollike on 2008-07-12
> **issih said:**
> Probably just hasn't created a launcher, open a terminal and type rub then hit tab a couple of times to see what programs start with rub, then view their man pages to work out what you want.

Alternatively reopen synaptic and locate the package you installed. select it and view the properties, in their is a list of the files it installed.

ewww lol!

---

### Post by Markissocoollike on 2008-07-12
> **kansasnoob said:**
> [ATTACH]77498[/ATTACH]

[http://www.trug.ca/Ruby_GUI_Toolkits](http://www.trug.ca/Ruby_GUI_Toolkits)

OMG I installed it still nothing under apps places and system D: :mad:

---

### Post by txcrackers on 2008-07-12
ruby is a command-line based program, so it will not appear in the menu.

---

### Post by Markissocoollike on 2008-07-12
> **txcrackers said:**
> ruby is a command-line based program, so it will not appear in the menu.

then where? Fat lot of use telling me that! I've done a search and I got a load of folders I found one with an exe extension but I can't run it... this os is driving me insane... just open! :(

---

### Post by Markissocoollike on 2008-07-12
where i'm going I'm probably gonna need to post so much that people will think that I'm spamming could someone just please tell me how to install it properly? I am not amused!

---

### Post by ibuclaw on 2008-07-12
**HowTo Use Ruby:** ;)

1) Create a file
```
gedit beer.rb
```
2) Put some sourcecode inside that file
```
class Integer # The bottles
  def drink; self - 1; end
end

class << song = nil
  attr_accessor :wall

  def bottles
    (@bottles.zero? ? "no more" : @bottles).to_s <<
      " bottle" << ("s" unless @bottles == 1).to_s
  end
  
  def of(bottles)
    @bottles = bottles
    (class << self; self; end).module_eval do
      define_method(:buy) { bottles }
    end
    self
  end
  
  def sing(&step)
    puts "#{bottles.capitalize} of beer on the wall, #{bottles} of beer."
    if @bottles.zero?
      print "Go to the store buy some more, "
      step = method :buy
    else
      print "Take one down and pass it around, "
    end
    @bottles = step[@bottles]
    puts "#{bottles} of beer on the wall."
    puts "" or wall.call unless step.kind_of? Method
  end

end

callcc { |song.wall| song.of(99) }.sing { |beer| beer.drink }
```
3) Save the file and quit.

4) Run the file with Ruby.
```
ruby beer.rb
```
It couldn't be any simpler!

HINT:
If you put the following
```
#!/usr/bin/ruby
```
At the top of every ruby source file you own. Then change the permissions of the file to allow execution
```
chmod +x beer.rb
```
You can run the file as is with a **./**
```
./beer.rb
```

Regards
Iain

---

### Post by Markissocoollike on 2008-07-12
> **tinivole said:**
> **HowTo Use Ruby:** ;)

1) Create a file
```
gedit beer.rb
```
2) Put some sourcecode inside that file
```
class Integer # The bottles
  def drink; self - 1; end
end

class << song = nil
  attr_accessor :wall

  def bottles
    (@bottles.zero? ? "no more" : @bottles).to_s <<
      " bottle" << ("s" unless @bottles == 1).to_s
  end
  
  def of(bottles)
    @bottles = bottles
    (class << self; self; end).module_eval do
      define_method(:buy) { bottles }
    end
    self
  end
  
  def sing(&step)
    puts "#{bottles.capitalize} of beer on the wall, #{bottles} of beer."
    if @bottles.zero?
      print "Go to the store buy some more, "
      step = method :buy
    else
      print "Take one down and pass it around, "
    end
    @bottles = step[@bottles]
    puts "#{bottles} of beer on the wall."
    puts "" or wall.call unless step.kind_of? Method
  end

end

callcc { |song.wall| song.of(99) }.sing { |beer| beer.drink }
```
3) Save the file and quit.

4) Run the file with Ruby.
```
ruby beer.rb
```
It couldn't be any simpler!

HINT:
If you put the following
```
#!/usr/bin/ruby
```
At the top of every ruby source file you own. Then change the permissions of the file to allow execution
```
chmod +x beer.rb
```
You can run the file as is with a **./**
```
./beer.rb
```

Regards
Iain

nice prank but still no ruby XD

---

### Post by Markissocoollike on 2008-07-12
Please Help Me!!!

---

### Post by ibuclaw on 2008-07-12
Is ruby installed?

```
which ruby || sudo apt-get install ruby
```
And thanks, there's a load more where that came from :D
[http://99-bottles-of-beer.net/](http://99-bottles-of-beer.net/)

Regards
Iain

---

### Post by jerome1232 on 2008-07-12
that's not a prank, copy the text into gedit save it as beer.rb
and run it with ruby, it does this:
```
$ ruby beer.rb
99 bottles of beer on the wall, 99 bottles of beer.
Take one down and pass it around, 98 bottles of beer on the wall.

98 bottles of beer on the wall, 98 bottles of beer.
Take one down and pass it around, 97 bottles of beer on the wall.

97 bottles of beer on the wall, 97 bottles of beer.
Take one down and pass it around, 96 bottles of beer on the wall.

96 bottles of beer on the wall, 96 bottles of beer.
Take one down and pass it around, 95 bottles of beer on the wall.

95 bottles of beer on the wall, 95 bottles of beer.
Take one down and pass it around, 94 bottles of beer on the wall.

94 bottles of beer on the wall, 94 bottles of beer.
Take one down and pass it around, 93 bottles of beer on the wall.

93 bottles of beer on the wall, 93 bottles of beer.
Take one down and pass it around, 92 bottles of beer on the wall.

92 bottles of beer on the wall, 92 bottles of beer.
Take one down and pass it around, 91 bottles of beer on the wall.

91 bottles of beer on the wall, 91 bottles of beer.
Take one down and pass it around, 90 bottles of beer on the wall.

90 bottles of beer on the wall, 90 bottles of beer.
Take one down and pass it around, 89 bottles of beer on the wall.

89 bottles of beer on the wall, 89 bottles of beer.
Take one down and pass it around, 88 bottles of beer on the wall.

88 bottles of beer on the wall, 88 bottles of beer.
Take one down and pass it around, 87 bottles of beer on the wall.

87 bottles of beer on the wall, 87 bottles of beer.
Take one down and pass it around, 86 bottles of beer on the wall.

86 bottles of beer on the wall, 86 bottles of beer.
Take one down and pass it around, 85 bottles of beer on the wall.

85 bottles of beer on the wall, 85 bottles of beer.
Take one down and pass it around, 84 bottles of beer on the wall.

84 bottles of beer on the wall, 84 bottles of beer.
Take one down and pass it around, 83 bottles of beer on the wall.

83 bottles of beer on the wall, 83 bottles of beer.
Take one down and pass it around, 82 bottles of beer on the wall.

82 bottles of beer on the wall, 82 bottles of beer.
Take one down and pass it around, 81 bottles of beer on the wall.

81 bottles of beer on the wall, 81 bottles of beer.
Take one down and pass it around, 80 bottles of beer on the wall.

80 bottles of beer on the wall, 80 bottles of beer.
Take one down and pass it around, 79 bottles of beer on the wall.

79 bottles of beer on the wall, 79 bottles of beer.
Take one down and pass it around, 78 bottles of beer on the wall.

78 bottles of beer on the wall, 78 bottles of beer.
Take one down and pass it around, 77 bottles of beer on the wall.

77 bottles of beer on the wall, 77 bottles of beer.
Take one down and pass it around, 76 bottles of beer on the wall.

76 bottles of beer on the wall, 76 bottles of beer.
Take one down and pass it around, 75 bottles of beer on the wall.

75 bottles of beer on the wall, 75 bottles of beer.
Take one down and pass it around, 74 bottles of beer on the wall.

74 bottles of beer on the wall, 74 bottles of beer.
Take one down and pass it around, 73 bottles of beer on the wall.

73 bottles of beer on the wall, 73 bottles of beer.
Take one down and pass it around, 72 bottles of beer on the wall.

72 bottles of beer on the wall, 72 bottles of beer.
Take one down and pass it around, 71 bottles of beer on the wall.

71 bottles of beer on the wall, 71 bottles of beer.
Take one down and pass it around, 70 bottles of beer on the wall.

70 bottles of beer on the wall, 70 bottles of beer.
Take one down and pass it around, 69 bottles of beer on the wall.

69 bottles of beer on the wall, 69 bottles of beer.
Take one down and pass it around, 68 bottles of beer on the wall.

68 bottles of beer on the wall, 68 bottles of beer.
Take one down and pass it around, 67 bottles of beer on the wall.

67 bottles of beer on the wall, 67 bottles of beer.
Take one down and pass it around, 66 bottles of beer on the wall.

66 bottles of beer on the wall, 66 bottles of beer.
Take one down and pass it around, 65 bottles of beer on the wall.

65 bottles of beer on the wall, 65 bottles of beer.
Take one down and pass it around, 64 bottles of beer on the wall.

64 bottles of beer on the wall, 64 bottles of beer.
Take one down and pass it around, 63 bottles of beer on the wall.

63 bottles of beer on the wall, 63 bottles of beer.
Take one down and pass it around, 62 bottles of beer on the wall.

62 bottles of beer on the wall, 62 bottles of beer.
Take one down and pass it around, 61 bottles of beer on the wall.

61 bottles of beer on the wall, 61 bottles of beer.
Take one down and pass it around, 60 bottles of beer on the wall.

60 bottles of beer on the wall, 60 bottles of beer.
Take one down and pass it around, 59 bottles of beer on the wall.

59 bottles of beer on the wall, 59 bottles of beer.
Take one down and pass it around, 58 bottles of beer on the wall.

58 bottles of beer on the wall, 58 bottles of beer.
Take one down and pass it around, 57 bottles of beer on the wall.

57 bottles of beer on the wall, 57 bottles of beer.
Take one down and pass it around, 56 bottles of beer on the wall.

56 bottles of beer on the wall, 56 bottles of beer.
Take one down and pass it around, 55 bottles of beer on the wall.

55 bottles of beer on the wall, 55 bottles of beer.
Take one down and pass it around, 54 bottles of beer on the wall.

54 bottles of beer on the wall, 54 bottles of beer.
Take one down and pass it around, 53 bottles of beer on the wall.

53 bottles of beer on the wall, 53 bottles of beer.
Take one down and pass it around, 52 bottles of beer on the wall.

52 bottles of beer on the wall, 52 bottles of beer.
Take one down and pass it around, 51 bottles of beer on the wall.

51 bottles of beer on the wall, 51 bottles of beer.
Take one down and pass it around, 50 bottles of beer on the wall.

50 bottles of beer on the wall, 50 bottles of beer.
Take one down and pass it around, 49 bottles of beer on the wall.

49 bottles of beer on the wall, 49 bottles of beer.
Take one down and pass it around, 48 bottles of beer on the wall.

48 bottles of beer on the wall, 48 bottles of beer.
Take one down and pass it around, 47 bottles of beer on the wall.

47 bottles of beer on the wall, 47 bottles of beer.
Take one down and pass it around, 46 bottles of beer on the wall.

46 bottles of beer on the wall, 46 bottles of beer.
Take one down and pass it around, 45 bottles of beer on the wall.

45 bottles of beer on the wall, 45 bottles of beer.
Take one down and pass it around, 44 bottles of beer on the wall.

44 bottles of beer on the wall, 44 bottles of beer.
Take one down and pass it around, 43 bottles of beer on the wall.

43 bottles of beer on the wall, 43 bottles of beer.
Take one down and pass it around, 42 bottles of beer on the wall.

42 bottles of beer on the wall, 42 bottles of beer.
Take one down and pass it around, 41 bottles of beer on the wall.

41 bottles of beer on the wall, 41 bottles of beer.
Take one down and pass it around, 40 bottles of beer on the wall.

40 bottles of beer on the wall, 40 bottles of beer.
Take one down and pass it around, 39 bottles of beer on the wall.

39 bottles of beer on the wall, 39 bottles of beer.
Take one down and pass it around, 38 bottles of beer on the wall.

38 bottles of beer on the wall, 38 bottles of beer.
Take one down and pass it around, 37 bottles of beer on the wall.

37 bottles of beer on the wall, 37 bottles of beer.
Take one down and pass it around, 36 bottles of beer on the wall.

36 bottles of beer on the wall, 36 bottles of beer.
Take one down and pass it around, 35 bottles of beer on the wall.

35 bottles of beer on the wall, 35 bottles of beer.
Take one down and pass it around, 34 bottles of beer on the wall.

34 bottles of beer on the wall, 34 bottles of beer.
Take one down and pass it around, 33 bottles of beer on the wall.

33 bottles of beer on the wall, 33 bottles of beer.
Take one down and pass it around, 32 bottles of beer on the wall.

32 bottles of beer on the wall, 32 bottles of beer.
Take one down and pass it around, 31 bottles of beer on the wall.

31 bottles of beer on the wall, 31 bottles of beer.
Take one down and pass it around, 30 bottles of beer on the wall.

30 bottles of beer on the wall, 30 bottles of beer.
Take one down and pass it around, 29 bottles of beer on the wall.

29 bottles of beer on the wall, 29 bottles of beer.
Take one down and pass it around, 28 bottles of beer on the wall.

28 bottles of beer on the wall, 28 bottles of beer.
Take one down and pass it around, 27 bottles of beer on the wall.

27 bottles of beer on the wall, 27 bottles of beer.
Take one down and pass it around, 26 bottles of beer on the wall.

26 bottles of beer on the wall, 26 bottles of beer.
Take one down and pass it around, 25 bottles of beer on the wall.

25 bottles of beer on the wall, 25 bottles of beer.
Take one down and pass it around, 24 bottles of beer on the wall.

24 bottles of beer on the wall, 24 bottles of beer.
Take one down and pass it around, 23 bottles of beer on the wall.

23 bottles of beer on the wall, 23 bottles of beer.
Take one down and pass it around, 22 bottles of beer on the wall.

22 bottles of beer on the wall, 22 bottles of beer.
Take one down and pass it around, 21 bottles of beer on the wall.

21 bottles of beer on the wall, 21 bottles of beer.
Take one down and pass it around, 20 bottles of beer on the wall.

20 bottles of beer on the wall, 20 bottles of beer.
Take one down and pass it around, 19 bottles of beer on the wall.

19 bottles of beer on the wall, 19 bottles of beer.
Take one down and pass it around, 18 bottles of beer on the wall.

18 bottles of beer on the wall, 18 bottles of beer.
Take one down and pass it around, 17 bottles of beer on the wall.

17 bottles of beer on the wall, 17 bottles of beer.
Take one down and pass it around, 16 bottles of beer on the wall.

16 bottles of beer on the wall, 16 bottles of beer.
Take one down and pass it around, 15 bottles of beer on the wall.

15 bottles of beer on the wall, 15 bottles of beer.
Take one down and pass it around, 14 bottles of beer on the wall.

14 bottles of beer on the wall, 14 bottles of beer.
Take one down and pass it around, 13 bottles of beer on the wall.

13 bottles of beer on the wall, 13 bottles of beer.
Take one down and pass it around, 12 bottles of beer on the wall.

12 bottles of beer on the wall, 12 bottles of beer.
Take one down and pass it around, 11 bottles of beer on the wall.

11 bottles of beer on the wall, 11 bottles of beer.
Take one down and pass it around, 10 bottles of beer on the wall.

10 bottles of beer on the wall, 10 bottles of beer.
Take one down and pass it around, 9 bottles of beer on the wall.

9 bottles of beer on the wall, 9 bottles of beer.
Take one down and pass it around, 8 bottles of beer on the wall.

8 bottles of beer on the wall, 8 bottles of beer.
Take one down and pass it around, 7 bottles of beer on the wall.

7 bottles of beer on the wall, 7 bottles of beer.
Take one down and pass it around, 6 bottles of beer on the wall.

6 bottles of beer on the wall, 6 bottles of beer.
Take one down and pass it around, 5 bottles of beer on the wall.

5 bottles of beer on the wall, 5 bottles of beer.
Take one down and pass it around, 4 bottles of beer on the wall.

4 bottles of beer on the wall, 4 bottles of beer.
Take one down and pass it around, 3 bottles of beer on the wall.

3 bottles of beer on the wall, 3 bottles of beer.
Take one down and pass it around, 2 bottles of beer on the wall.

2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around, 1 bottle of beer on the wall.

1 bottle of beer on the wall, 1 bottle of beer.
Take one down and pass it around, no more bottles of beer on the wall.

No more bottles of beer on the wall, no more bottles of beer.
Go to the store buy some more, 99 bottles of beer on the wall.

```

that would be a ruby program

edit: (lol like the program btw)

---

### Post by AnLGP on 2008-07-12
:lolflag:

I'm gonna run that.  That's great.  Then I'll rewrite it myself.  Thanks for that it'll teach me something.

---

### Post by Markissocoollike on 2008-07-12
> **tinivole said:**
> Is ruby installed?

```
which ruby || sudo apt-get install ruby
```
And thanks, there's a load more where that came from :D
[http://99-bottles-of-beer.net/](http://99-bottles-of-beer.net/)

Regards
Iain

no... and could you guys get to the matter at hand please *groans*

---

### Post by ibuclaw on 2008-07-12
Are you sure that you are a Ruby Programmer?

If you follow my instructions precisely, it will happen.
Trust me, other people have "made it work".

Also, can you post the output of the commands I give you.
It would help very much and we would be able to track down your problem much quicker. ("It doesn't work" and "*groans*" will not help me see what you are seeing ;) )

Have you saved the sourcecode I put up to a file?
If you, where is it?
```
ls beer.rb
```
And what was the output of:
```
which ruby
```
?

Regards
Iain

---

### Post by Markissocoollike on 2008-07-12
> **tinivole said:**
> Are you sure that you are a Ruby Programmer?

If you follow my instructions precisely, it will happen.
Trust me, other people have "made it work".

Also, can you post the output of the commands I give you.
It would help very much and we would be able to track down your problem much quicker.

Have you saved the sourcecode I put up to a file?
If you, where is it?
```
ls beer.rb
```
And what was the output of:
```
which ruby
```
?

Regards
Iain

It ran with the terminal but i still do not see no ruby

---

### Post by Markissocoollike on 2008-07-12
your file is on desktop :lolflag:

---

### Post by ibuclaw on 2008-07-12
So the 99 bottles of beer worked then?

As has been said in this thread earlier. Ruby is a terminal app.
You use it by putting sourcecode in a file using your favourite editor (**vim FTW!!!**) and then run the source by typing in:
```
ruby **filename**.rb
```
or if you put **#!/usr/bin/ruby** at the top of the file
```
./**filename**.rb
```
[EDIT]
Also, you need to **cd** to the file location first if it isn't stored inside one of your $PATH paths. (To find out where they are type in "**echo $PATH**")

I think what you are confusing Ruby for is an IDE.
So lets clear one thing up. Ruby is not an IDE.

If an IDE is what you are looking for, then just say so. There are quite a few out there that you'll have to try out to see if it suits your needs.

Regards
Iain

---

### Post by Markissocoollike on 2008-07-12
I tried echo ruby and it just said ruby lolz

I tried #!/usr/bin/ruby nothing happened is linux really this complicated?

---

### Post by nothingspecial on 2008-07-12
> **Markissocoollike said:**
> is linux really this complicated?

No, night night=;

---

### Post by Markissocoollike on 2008-07-12
> **nothingspecial said:**
> No, night night=;

prrf yeh right...

---

### Post by estyles on 2008-07-12
This thread is insane.  I'm surprised no one has asked why in the heck you want to install Ruby...  You don't seem like you're a programmer or have any interest at all in programming.

As for the "paranoid" security...  having to type in your password once in a while when modifying system-essential files is not a hardship.  Having your entire HD wiped by viruses because you're running in Administrator mode is.  If you don't believe me, run Windows as an Administrator for a couple months and download everything you see.

---

### Post by ibuclaw on 2008-07-12
So the top of the file looks like this?
```

#!/usr/bin/ruby
class Integer # The bottles
  def drink; self - 1; end
end
...
...

```
And you set the file to have execute permissions?
```
chmod +x beer.rb
./beer.rb
```
Again, are you sure that you are a Ruby programmer?

> **estyles said:**
> This thread is insane.  I'm surprised no one has asked why in the heck you want to install Ruby...  You don't seem like you're a programmer or have any interest at all in programming.

I'm not that rude. But I have asked on quite a few occasions the legitimacy of his programming knowledge. He has yet to reply... :(

> 
As for the "paranoid" security...  having to type in your password once in a while when modifying system-essential files is not a hardship.  Having your entire HD wiped by viruses because you're running in Administrator mode is.  If you don't believe me, run Windows as an Administrator for a couple months and download everything you see.
Months???

Try a few days with a family computer ;)

Regards
Iain
[EDIT]
1,100 Posts!

You are on your own...

---

### Post by kansasnoob on 2008-07-12
How is this helpful to anyone now?

---

### Post by Markissocoollike on 2008-07-12
sigh, I give up, this stupid os doesn't want me to have ruby obviously, i've tried many tutorials on how to install it and nothing I have to face the fact that I can't have this program... why would anyone program something that can't even let me install the programs I want is beyond me... the os is great but an appropriate start menu would be nice but I wouldn't recommend this os for beginners this os has some bugs which need fixing

---

### Post by glarnewbie on 2008-07-12
Hello,
If I read your initial post correctly, you are trying to un-tar a .zip file, which is why the first error "File not found" comes up.  If this fact has already been addressed, and I just missed it, then my apologies for a duplicate post.

---

### Post by aktiwers on 2008-07-12
Are you expecting a GUI program for ruby?
I am no ruby programmer, but I have seen this is out there. If this is the case, you might ask the ruby programmers here what the name is, because it seams like the ruby you installed is without GUI.

---

### Post by ChameleonDave on 2008-07-12
> **tinivole said:**
> **HowTo Use Ruby:** ;)

...
Iain

That's fantastic!  I've been to that site, and noticed that out of the 1207 programming languages, they are missing one that I know!  I shall write the song in it immediately!

To the original poster:  You don't know ruby, and are not going to use it, so it would be best not to waste people's time by having them help you install it.

---

### Post by ChameleonDave on 2008-07-12
> **Markissocoollike said:**
> sigh, I give up, this stupid os doesn't want me to have ruby obviously, i've tried many tutorials on how to install it and nothing I have to face the fact that I can't have this program... why would anyone program something that can't even let me install the programs I want is beyond me... the os is great but an appropriate start menu would be nice but I wouldn't recommend this os for beginners this os has some bugs which need fixing
You're joking, right?

---

### Post by jerome1232 on 2008-07-12
[http://ubuntuforums.org/showthread.php?t=857390&page=3](http://ubuntuforums.org/showthread.php?t=857390&page=3)

found out why he wanted ruby...

---

### Post by mdsmedia on 2008-07-12
I'm not a programmer, in Ruby or anything else, but all I've seen from the OP so far is an apology for being rude (first post) then idiotic non-sensical questions and absolutely no assistance to the people trying to help him, and rudeness.

If you are going to be rude, don't apologise for it first then go and be rude, just don't be rude.

As I said, I'm not a programmer, but I think just from this thread I have more idea of Ruby than the OP does.

---

### Post by TSS on 2008-07-12
```
echo "If it looks like a chicken and walks like a chicken..." | sed 's/chicken/troll/g'
```

---

### Post by ChameleonDave on 2008-07-12
> **TSS said:**
> ```
echo "If it looks like a chicken and walks like a chicken..." | sed 's/chicken/troll/g'
```
Yeah, I thought that.  But the fact is that human beings are quite capable, through sheer cluelessness, of mindlessly doing things which appear to any observer to be the result of malice.  Just look at Iraq!

I think we might have the answer to this if we ask the OP's age. ;-)

---

### Post by ad_267 on 2008-07-12
> **Markissocoollike said:**
> sigh, I give up, this stupid os doesn't want me to have ruby obviously, i've tried many tutorials on how to install it and nothing I have to face the fact that I can't have this program... why would anyone program something that can't even let me install the programs I want is beyond me... the os is great but an appropriate start menu would be nice but I wouldn't recommend this os for beginners this os has some bugs which need fixing

Wow, go back to windows then.

What do you expect to see when you run ruby? Do you even know what ruby is? You have installed ruby and it's doing what it's supposed to do. You just don't seem to even know what ruby is.

---

### Post by madsmeg on 2008-07-12
> I think we might have the answer to this if we ask the OP's age

Heh, your thinking what i am thinking.

This is nearly as fun to read as the guy that hosed his dads system because "linux looked cool"

---

### Post by jerome1232 on 2008-07-12
> **madsmeg said:**
> Heh, your thinking what i am thinking.

This is nearly as fun to read as the guy that hosed his dads system because "linux looked cool"

You have a link? I'm pretty bored.

---

### Post by ibuclaw on 2008-07-12
> **ChameleonDave said:**
> That's fantastic!  I've been to that site, and noticed that out of the 1207 programming languages, they are missing one that I know!  I shall write the song in it immediately!

To the original poster:  You don't know ruby, and are not going to use it, so it would be best not to waste people's time by having them help you install it.
Which language would that be?

---

### Post by madsmeg on 2008-07-12
no, but now i want to find it...

---

### Post by ibuclaw on 2008-07-12
> **mdsmedia said:**
> I'm not a programmer, in Ruby or anything else, but all I've seen from the OP so far is an apology for being rude (first post) then idiotic non-sensical questions and absolutely no assistance to the people trying to help him, and rudeness.

If you are going to be rude, don't apologise for it first then go and be rude, just don't be rude.

As I said, I'm not a programmer, but I think just from this thread I have more idea of Ruby than the OP does.
Have you seen my simple walkthrough?

[http://ubuntuforums.org/showpost.php?p=5373086&postcount=15](http://ubuntuforums.org/showpost.php?p=5373086&postcount=15)

If at all you refer to me, I don't feel that I'm being rude in the slightest.

Perhaps my only mistake would be the assumption that he was indeed a Ruby Programmer, afterall, even on Windows, Ruby Programmers know how to run their own code. The way you do it in Linux is really no different.

I know there have been the odd heckles; but I have frequently asked the OP of his knowledge about Ruby. I have asked him to post the output of the commands I give him.

But alas, no feedback == no result!

If he truly wanted it to work, he would have allowed himself to help me too.

Regards
Iain

---

### Post by LaRoza on 2008-07-12
Put this command in the terminal. If you get vastly different output, post it here.

```

~$ruby -v
ruby 1.8.6 (2007-09-24 patchlevel 111) [i486-linux]
~$

```
If the above worked, do this one:
```

~$echo "puts 'hello world'" > p.rb && chmod +x p.rb && ruby p.rb
hello world
~$

```

(That code just makes a file named "p.rb", puts some code into, marks it as executable and runs it with ruby)

If that doesn't work, copy and paste the error.

---

### Post by Bodsda on 2008-07-12
Did he install the correct ruby package? 

Does ruby have an interactive prompt like python?

```
python
>>> print "Hello World"
Hello World
>>>
```

---

### Post by ChameleonDave on 2008-07-12
> **LaRoza said:**
> Put this command in the terminal. If you get vastly different output, post it here.

```

~$ruby -v
ruby 1.8.6 (2007-09-24 patchlevel 111) [i486-linux]
~$

```If the above worked, do this one:
```

~$echo "puts 'hello world'" > p.rb && chmod +x p.rb && ruby p.rb
hello world
~$

```(That code just makes a file named "p.rb", puts some code into, marks it as executable and runs it with ruby)

If that doesn't work, copy and paste the error.
Let's get this straight.  There is no point posting examples to help the original poster use Ruby.  He installed it because he heard someone say that he could configure the cube with it, but he doesn't realise that he has installed it, he doesn't know what a programming language is, he doesn't understand that some software is command-line only, and doesn't understand what any of us are talking about.  The thread ought to be closed, in fact.

---

### Post by AnLGP on 2008-07-12
visit [http://www.ruby-lang.org](http://www.ruby-lang.org) to learn about Ruby.  There are various tutorials on the net for what it can accomplish.  It is an object oriented programming language (as a newb in programming I'm still learning what that means).  The program suggested earlier (the beer one) works fine.  That's what Ruby does.  If you were able to run that program (beer.rb) you have Ruby installed.

---

### Post by LaRoza on 2008-07-12
> **Bodsda said:**
> Did he install the correct ruby package? 

Does ruby have an interactive prompt like python?

```
python
>>> print "Hello World"
Hello World
>>>
```

Yes, irb. 

```

sudo aptitude install irb

~$irb
irb(main):001:0> puts "Hello world"
Hello world
=> nil
irb(main):002:0> 


```


> **ChameleonDave said:**
> Let's get this straight.  There is no point posting examples to help the original poster use Ruby. The thread ought to be closed, in fact.

It came to my attention because of reports. Since this thread is no long abour tech support, it is being moved to Cafe.

---

### Post by mdsmedia on 2008-07-12
> **tinivole said:**
> Have you seen my simple walkthrough?

[http://ubuntuforums.org/showpost.php?p=5373086&postcount=15](http://ubuntuforums.org/showpost.php?p=5373086&postcount=15)

If at all you refer to me, I don't feel that I'm being rude in the slightest.

Perhaps my only mistake would be the assumption that he was indeed a Ruby Programmer, afterall, even on Windows, Ruby Programmers know how to run their own code. The way you do it in Linux is really no different.

I know there have been the odd heckles; but I have frequently asked the OP of his knowledge about Ruby. I have asked him to post the output of the commands I give him.

But alas, no feedback == no result!

If he truly wanted it to work, he would have allowed himself to help me too.

Regards
IainNo, your attempts at assistance were not rude in the slightest. I was referring to the OP. I was thinking of thanking you on his behalf a few times just because i thought your posts were great. I learned something even though I'm not a programmer lol. :)

---

### Post by ibuclaw on 2008-07-12
> **mdsmedia said:**
> No, your attempts at assistance were not rude in the slightest. I was referring to the OP. I was thinking of thanking you on his behalf a few times just because i thought your posts were great. I learned something even though I'm not a programmer lol. :)

Thanks man, that's is well appreciated.

Unfortunately, I've stumbled across this link.
[http://ubuntuforums.org/showpost.php?p=5372920&postcount=29](http://ubuntuforums.org/showpost.php?p=5372920&postcount=29)

I believe this entire episode has been a major breakdown in communication. All because the wrong terminology was used in the first place.

> well according to this guy I can change the GUI with ruby...might as well try!
I'm thinking he meant Ruby, as in the age old icon for the Beryl/Emerald Desktop.

This really disappoints me, not because I didn't find it earlier, but because the OP never even explained the purposes of his intent for the correction to be made.

It's not like he didn't have any chance to say it. He just didn't say it.

But I will be rather upset at this when the day ends. :(

Iain

---

### Post by cariboo on 2008-07-12
We should all have a look at his guy, at times he displays more knowledge that the newbie he professes to be, a couple of post before the post that tinivole quoted he posted a code block where he was inatalling build-essential and then trying to install ruby from source. Then he went on to complian that there was no shortcut in the menu to ruby. I personally think we are being trolled.

Jim

---

### Post by k3lt01 on 2008-07-12
cariboo/Jim your right we are being trolled and I wonder to myself why people have been feeding the troll for so long. I have been watching this and his other thread where he has been posting furiously, to see his post count go up at a rapid rate of knots, it was over 40 at one stage, now it has dropped back down to 27. Hmmmmm.

Oh well I learned something out of this, I liked the 99 Bottles of Beer posts in these threads.

---

### Post by LaRoza on 2008-07-12
> **k3lt01 said:**
> I have been watching this and his other thread where he has been posting furiously, to see his post count go up at a rapid rate of knots, it was over 40 at one stage, now it has dropped back down to 27. Hmmmmm.


When I saw the threads were not support threads, I moved them here (Cafe). That would remove the post count as posts aren't counted in the Cafe.

---

### Post by k3lt01 on 2008-07-12
Aha, that explains it, thanks LaRoza I have learned 2 things now in these threads.

---

### Post by estyles on 2008-07-13
> **mdsmedia said:**
> No, your attempts at assistance were not rude in the slightest. I was referring to the OP. I was thinking of thanking you on his behalf a few times just because i thought your posts were great. I learned something even though I'm not a programmer lol. :)

Agreed - your posts were very helpful for someone who legitmately wanted to install Ruby.

The OP was either a troll who had no intention or reason to install Ruby, or else a newbie (nothing wrong with newbies, I admit to being one myself) who had jumped in way, WAY over his head - in which case, more than instructions on how to install the Ruby package, he needs/needed some guidance on what his end goal is and why he thinks he needs Ruby to achieve it.

I'm thinking the troll thing is most likely.  Reading his thread on the "security paranoia" where he complains about having to enter his password a few times (hell, if you're entering your password every 30 seconds, you're doing something wrong - how many weird things are you trying to install???)...  well, if he isn't a troll, then I think maybe he just needs to deal with a different OS for a while and maybe will come back to Linux when he reaches his teens.

---

### Post by LaRoza on 2008-07-13
> **estyles said:**
> well, if he isn't a troll, then I think maybe he just needs to deal with a different OS for a while and maybe will come back to Linux when he reaches his teens.

Read where she says "Linux should be more like Windows" ;)

---

### Post by Jim! on 2008-07-13
> **Markissocoollike said:**
> 
in the meantime how do I disable the stupid password security it is getting on my nerves (i've been entering it over and over again for every installation I attempt!)
Just a general tip, when your typing commands in the terminal you can press "Ctrl + R" to bring up a recent command.

---

### Post by LaRoza on 2008-07-13
> **Jim! said:**
> Just a general tip, when your typing commands in the terminal you can press "Ctrl + R" to bring up a recent command.

Or up arrow.

---

### Post by bapoumba on 2008-07-13
> **Jim! said:**
> Just a general tip, when your typing commands in the terminal you can press "Ctrl + R" to bring up a recent command.

> **LaRoza said:**
> Or up arrow.
I use CTRL-R when I need a command I know I typed a while ago. With a few letters, no matter where they are in the command, it will retrieve it:
```
(reverse-i-search)`ing': sudo /etc/init.d/networking restart
```
Up arrow is good for a command you typed just a few commands ago :)

Thanks to everyone who answered in this thread, gave time and input, it is much appreciated. This thread is going nowhere, really, so I'm closing.

---

