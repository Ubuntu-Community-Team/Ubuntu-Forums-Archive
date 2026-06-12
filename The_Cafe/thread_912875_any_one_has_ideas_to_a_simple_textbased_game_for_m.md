---
title: "any one has ideas to a simple textbased game for my brother."
date: 2008-09-07
forum: The Cafe
---

### Post by cmay on 2008-09-07
hi.
i want to write a simple textbased game for my brother. he was playing a game all the time on windows that had the simple gameplay that the player should hack into a bank account to win. i personally dont like this concept that much but as a exiting gameplay in a text based game that i can write it could do. a bit against my will however.i need however some good ideas and maybe some hints on how to make a real fun game for my brother. however i am not full of ideas as of what a textbased game could be like if it should be fun and a bit "cool" to play. and it has to be a text game. i am trying out my very low programming skills for the max on this.
any ideas for a nice little text game.?
thanks for your input :)

---

### Post by elmer_42 on 2008-09-07
I've made a few text-based games in Ruby. I would look into both Ruby and Python and decide which one would better suit your game.

---

### Post by lukjad on 2008-09-07
Look at a game like NetHack for ideas. The trick with text based games is that they have to be unpredictable and funny.

---

### Post by cmay on 2008-09-07
> I've made a few text-based games in Ruby. I would look into both Ruby and Python and decide which one would better suit your game.
thanks for the reply. what kind of game did you write. was it adventure games and how did you make the games fun to play ?. i cant think of anything really new and original as story for the game. i want to write it so that it is fun to play more than once but i am not very good at programming yet.(or at getting original ideas for games) so i will just keep it in the console.

---

### Post by cmay on 2008-09-07
> Look at a game like NetHack for ideas. The trick with text based games is that they have to be unpredictable and funny.
i think it was actually that game my brother was playing constantly for a while but i thought it was a windows only game. if its possible to get for linux i could try play it a bit so i can maybe get some ideas from it. 

thanks.

---

### Post by lukjad on 2008-09-07
Try to make a parody of or take some ideas from the Lord Of The Rings story. It may be just the push you need to create the backstory. Also, try to write a little story and some cheat codes for a little fun. (If you feel like it.)

---

### Post by lukjad on 2008-09-07
NetHack has nothing to do with Bank BTW. Also, there is a GUI for NetHack called QT NetHack if you want to test the waters without staring at a command prompt.

---

### Post by cmay on 2008-09-07
> Try to make a parody of or take some ideas from the Lord Of The Rings story. It may be just the push you need to create the backstory. Also, try to write a little story and some cheat codes for a little fun. (If you feel like it.)
 that could work. or steal the story from starwars maybe. i think i may have some ideas now.  is ruby easy to use for games. and what do i need. i would not mind honestly to have a simple background picture as intro and i dont know how to use sound or pictures yet. i had trouble the first time i tried to make a game in pascal since there was really not that many other options than using allegro and i was just learning at the time so it did not work out for me then.

---

### Post by lukjad on 2008-09-07
Whatever you do come up with, please, post a link to it. I would be very interested to see what you come up with. :)

---

### Post by cmay on 2008-09-07
i will post it when i am done. if it works. i have other things i may post some time as well like sounds i am making and icons i have made a while ago. i have a little home studio so making sound effects is no problem but i have yet to learn to use them in programming . i will start writing a story tonight and code when i can then i will post all i got when i hopefully are done. thanks for your time.

---

### Post by lukjad on 2008-09-07
If you like, just post the story and I'd be happy to give you some feedback.

---

### Post by cmay on 2008-09-07
i could do that. i have already sort of getting some ideas. i could try to make up a story that is taking place in the future in a spaceship  so the console game play maybe works almost realistic. i wish i knew how to work whit pictures and sound but i think i just cook something up from all my space movies as inspiration. :)

---

### Post by lukjad on 2008-09-07
May the Force be with you.

---

### Post by linuxguymarshall on 2008-09-07
I like to make text-based games in BASIC. Look for them

---

### Post by elmer_42 on 2008-09-07
> **cmay said:**
> what kind of game did you write. was it adventure games and how did you make the games fun to play ?
The game started of as a joke between my friends when we saw a book called "World of Shakespeare" at Borders. We, being the geeks we are, instantly though, "World of Shakespeare, is that anything like World of Warcraft?" and thus the game was born. Come to think of it, I'm actually still working on it, because I got a little bored with it and stopped. It will eventually involve various encounters with Shakespearean characters. The actual game itself is pretty scripted, that is, you can't really explore, because once I figured out how to make it save using YAML I went off and played with YAML for a while. I can always implement exploring in the future.

And here I am now, wanting to work on it some more. I just checked, and there's actually only one little scene in it. Wow. I thought I was more finished with this than I actually am. If you want me to put the source up somewhere, I can, just give me a shout. I'm going to be fly-fishing most of the day, though, so I'll check back later.

**e:**Oh, I found a thing that may help. It's a sort of text-game coding challenge. I don't think my version actually works any more, because I tried to do something that was stupid to a perfectly good version of it, but there is a Ruby version that has no frills that may help you. Check it out [here]("http://wiki.hak5.org/wiki/Text_Game").

---

### Post by cmay on 2008-09-07
thanks.

---

### Post by gletob on 2008-09-07
> **lukjad007 said:**
> May the Force be with you.

May the Source be with you

---

### Post by lukjad on 2008-09-07
> **gletob said:**
> May the Source be with you
Compromise:
May the Forge be with you.

---

### Post by billgoldberg on 2008-09-07
Ah, text based games.

We used to have fun with those on our graphical calculators with the big screens (Texas Instr.) back in school.

Some dude even had some x-rated games.

---

### Post by lukjad on 2008-09-07
> **billgoldberg said:**
> Some dude even had some x-rated games.
I don't wanna know...

---

### Post by cmay on 2008-09-07
ok:
just to let everyone know i am going to work on it .
here is the first draft for the game play structure in c. the language i am learning now and i want to use if not pascal. its going to take time and this is just a very very very simple test i made. my brother is starting to write a manual for me for his cardboard game he just made and will be happy if i write it as a computer game. i have never written a game at all before other than the traditional guess my secret number game. so i will may have some design troubles i guess. but i think i go for this idea with a choice that one has to write as a word and not just use single keys to play the game.

 of course i do not count life or weapons in this test version and its going to be divided into header files also. and the game is very short also . i will post the final version when its done if i can get it to work . 
[PHP]
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

void help();
void quit();
int game_demo();
int intro();
int main(int argc,char **argv)
{
char read_stdin[100];

do
{
	
	if(strcmp(read_stdin,"--play\n")==0)
	   {
	  	game_demo();
	   }
    if(strcmp("--exit\n",read_stdin)==0)
       {
       quit();
       }
    if(strcmp("--help\n",read_stdin)==0)
       {
       help();
       }
    
       printf("options --help --play --exit\n");
 }
while(fgets(read_stdin,(sizeof read_stdin),stdin));

return 0;
}
/**********************: end main :*******************/
void help()
{
	char text[]="******************\n"
	            "* The TITLE      *\n"
	            "******************\n"
	            " help file coming here soon please be patient \n";
	            printf("%s",text); 	         
} 
void quit()
{
	printf("thanks for playing \nplease play again some time\n");
	abort();
}


int game_demo()
{
	char choice[50];
	intro();
	getchar();
	system("clear");
	printf("you are contronted by an evil evil evil beast !! what do you do\?\n");
	printf("[run] [fight]\n");
	while(1)
	{
		fgets(choice,(sizeof choice),stdin);
	if(strcmp("run\n",choice)==0)
	  {
	  printf("good choice you win\n");
	  printf("try again \?\n");
	  return 1;
     }
	if(strcmp("fight\n",choice)==0)
	{
	  printf("stupid choice you loose\n");
	  printf("try again\?\n");
	  return 1;
	}
	else printf("invalid input try again\n");
    }
return 0;
}  
	
int intro()
{
	char intro_text[]="\n"
	"in the year 2200 the earht is a cold planet whitout life\n"
	"all the remaining earthlings has been picked up by spacelings.\n"
	"it is a gruesome scenario where humans fight the evil evil evil dvorks\n"
	"in alliance whit their spacey companions the quirgs\n"
	"\n"
	"your misson is to find a cure for the coldness of the planet earth\n"
	"and bring it back to life. you have to singel handedly fight lots of evil monstres \n"
	"and find a vaccine for healing your people back on earht. \n\nwearing spacesuits to keep them warm\n"
	"\n""LET THE GAME BEGIN!!!\n";
	printf("%s",intro_text);
return 0;
}
[/PHP]
just compile with gcc -Wall -std=c99  if the urge to play a very useless demo of my game comes over anyone :)

and thanks for your input everyone.

---

### Post by joninkrakow on 2008-09-07
> **cmay said:**
> i could do that. i have already sort of getting some ideas. i could try to make up a story that is taking place in the future in a spaceship  so the console game play maybe works almost realistic. i wish i knew how to work whit pictures and sound but i think i just cook something up from all my space movies as inspiration. :)

I've got an idea for you. It's already a game, but it's a first-person shooter from the dark ages of computerdom. However, its story was played out in computer consoles that you, the player read during the game. You could start from these terminal screens, and build your game. The added benefit is that you will almost have a built-in player community if you do a good job, The Marathon game has quite a rabid following, despite it's almost 15 years of age. There's still a web site devoted to its story line. You can read it all here, and start your coding immediately. ;-)

[Marathon Story Page]("http://marathon.bungie.org/story/")

Personally, I would be interested in a text-based game, based on Marathon. BTW, I highly recommend playing the game. Bungie (yes, the Halo guys) released the source when they were bought by Microsoft, and it's been ported to Linux, and there is a rpm available for it (though I haven't gotten it running yet on Ubuntu). Play through all three games (Marathon, Durandal and Infinity) and then, maybe, extend the story, coming up with a way to tie it into Halo. (My personal theory is that Durandal and you both discover the flood, and the means to "destroy" them with the rings--you are the forerunner--and the John 117 in Halo. ;-)  )

Anyway, there's a LOT of play value in Marathon for a text-based game.

-Jon

---

### Post by cmay on 2008-09-07
> I've got an idea for you. It's already a game, but it's a first-person shooter from the dark ages of computerdom. However, its story was played out in computer consoles that you, the player read during the game. You could start from these terminal screens, and build your game. The added benefit is that you will almost have a built-in player community if you do a good job, The Marathon game has quite a rabid following, despite it's almost 15 years of age. There's still a web site devoted to its story line. You can read it all here, and start your coding immediately.

Marathon Story Page
thanks i will check this out. i am not sure how easy it will be. you can see my first attempt above. but i need some easy storyboard for the game so i may use something that is already there. as it also happens my brother has for some reason created a cardboard game he would like me to try translate into a computer game. i can use all the coding experience i get so i may end up doing them both and then solve all the problems in the kerninghan c programmering language as well. i have just started a month ago .

thanks for the time.

---

### Post by lukjad on 2008-09-12
Any storyline yet?

---

### Post by cmay on 2008-09-13
no storyline yet. just a simple two level test game.very simple and boring. my brother should have mailed me the story but he forgot it. i have however written lots of small test and i hope i can count on my brother to write the story for the game as i am trying to write it for him. i will post here when i get something done that is playable. this weekend i hope i am going to start being productive. i have also found links to other text based games i can study. all i need really is a creative little brother that can write me a story board for an text based alien game. i still would consider all other suggestions that comes along :)
i talk with him today and we are hopefully going to write the story and plan it over email so i can start writing by tonight. 
i will post results here. and thanks for the interrest.

---

### Post by lukjad on 2008-09-13
If you are doing it about aliens, why not have a "hook"? Do something out of the ordinary. I cannot post it here since everyone would know but I'll PM you if you like.

---

### Post by cmay on 2008-09-13
i would be very happy for any help.
here is  what i done so far even if its not that much and if somethings are not going to be used.
 i just made a function header that works for a part of the story. i imagine that i want to have a part of the story take place in a spaceship where the player has to connect to other computers to retrieve some informations. so i made a little simulator for that part just now. 

other than that i just study other text games to find out how to write a game.

 my brother has also a story he promised to send me and he promised to write the part of the stories in txt files that i already made a calling function for displaying in the terminal. so that when something happens that needs to be printed as text on screen i can just call it by name.txt when it is needed .and then one can change the game story translate if need just by changing  contents of the txt.files. if it works as i plan it will.

 that is what i have done so far.  and the above code for the actual game
 menu it self. its going to be invoked in bash ./game -p for play or ./game -h for help and if just it invoked ./game there is a promt that displays  options --play --help or --exit. 
that was the easy part. the story and game is more tricky. please feel free to pm any suggestions. i am however still learning c and it is what i write it in so i cant promise any great results but i will post it here when done. i am writing on it right now. so in a matter of few hours i can say if i have future as game developer or not :)

---

### Post by cmay on 2008-09-13
this is the story line my brother sent me. i will see how good a game in that style i can come up with and i will post the final result when done.
a little fun alien adventure is seems to become hopefully.
```
Genre:               Sci-Fi
Style:                  Text-based, adventure.
Title:                   The Lost Years

Story (basics)

Trent Welkins, the main character wakes up on the spaceship (USS Serenity), unknowing of his surroundings he starts exploring the ship.

(This will be the prologue, where you make a mini-game to get the player involved in the game play story and to set the initial mood of the environment)

Making a breathtaking escape from the monster onboard the ship, he finds himself at a console. When he tries to enter the computer he is prompted with and Artificial Intelligence that wants to make sure that he is indeed human. (This will also open the opportunity that others have tried to access the console (others! Ohhh&#8230; scary aye?)

When the &#8220;mission&#8221; has been solved, he now can control the ships life system. During his exploring on the console he discovers that there are other people on the ship, however they are completely unaware of his presence. Now there&#8217;s a question of saving these people from alien invaders using the airlock doors (which have to be &#8220;hacked&#8221;) and other measures. Trent himself will of course also have problems with avoiding the aliens.

He will have 3 main missions!

1 &#8211; Save as many of the surviving people onboard the ship.

2 &#8211; Destroy the alien invaders

3 &#8211; Escape the ship
```

edit:
[http://brothersofmai.frac.dk/news.php](http://brothersofmai.frac.dk/news.php)
and he has announced it on his homepage as well.

---

