---
title: "Order Pizza from your CLI!"
date: 2008-06-21
forum: The Cafe
---

### Post by azurepancake on 2008-06-21
I am not sure just how popular this is, but I just came across this and I was a bit skeptical at first, but I actually want to give it a shot now, after reading a couple articles about it.

What it does it pretty straight forward. It lets you order pizza straight from your terminal! Check out these links.. 

[http://www.youtube.com/watch?v=x7pPajOvQGo](http://www.youtube.com/watch?v=x7pPajOvQGo)
[http://www.linux.com/articles/113693](http://www.linux.com/articles/113693)
[http://www.beigerecords.com/cory/pizza_party/](http://www.beigerecords.com/cory/pizza_party/)

---

### Post by bufsabre666 on 2008-06-21
mmm.... cli pizza

but why is there a verbose command? so you can watch the process? 
does force make it so you dont have to pay?
how come no drink ordering command? i like a dr pepper or mt dew with my pizza personally

---

### Post by chris4585 on 2008-06-21
I want cli pizza now...

---

### Post by lisati on 2008-06-21
sudo apt-get free-pizza

---

### Post by schauerlich on 2008-06-21
You want a clip of izza? Okay... I guess...

[http://www.youtube.com/watch?v=BWVKa9DL-UI](http://www.youtube.com/watch?v=BWVKa9DL-UI)


Anon always delivers.

---

### Post by aggiemarine07 on 2008-06-21
How can I get that installed on my system? It lists the dependencies in the README but I can not find them in ubuntu repositories, are they listed as something else? Here are the listed dependencies below:

LWP::UserAgent;
      HTTP::Request;
      HTTP::Response;
      HTTP::Cookies;
      URI::Escape;
      Getopt::Mixed;

Thanks in advance!

---

### Post by azurepancake on 2008-06-21
> **aggiemarine07 said:**
> How can I get that installed on my system? It lists the dependencies in the README but I can not find them in ubuntu repositories, are they listed as something else? Here are the listed dependencies below:

LWP::UserAgent;
      HTTP::Request;
      HTTP::Response;
      HTTP::Cookies;
      URI::Escape;
      Getopt::Mixed;

Thanks in advance!

If your using Ubuntu Hardy, then the only package you need to install is libgetopt-mixed-perl..

```
sudo apt-get install libgetopt-mixed-perl
``` 

You can then run it straight from the directory..

```
./pizza_party
```

Or you can do what I did (and is recommended in the README) and move the "pizza_party" file to the '/usr/local/bin' directory..

```
sudo mv pizza_party /usr/local/bin
```

Then you can move the man file to the '/usr/local/man/man1' directory..

```
sudo mv man /usr/local/man/man1
```

Now you can just type..

```
pizza_party
``` 

..into the terminal to start the program. If you read the man page, you can create a configuration file called ".pizza_partyrc" in your /home/user directory. Here is the template..

```

       username=rtm
       password=simple
       default_quantity=3
       default_size=medium
       default_crust=deep
       default_toppings=pmx

```

Enjoy and have fun!

---

### Post by zachtib on 2008-06-21
where's the --no-cheese flag?

---

### Post by Mateo on 2008-06-21
> **zachtib said:**
> where's the --no-cheese flag?

Then it wouldn't be a pizza, would it?

---

### Post by cardinals_fan on 2008-06-21
```
pacman -Sy
pacman -S crust-thick
pacman -S chicken
pacman -S barbequesauce
pacman -S onions
pacman -S garlic
pacman -S pineapple
```
The perfect pizza :)

---

### Post by magnus0 on 2008-06-21
```
sudo apt-get pizza -cheese -chicken -pineapple -garlic

```
lol

---

### Post by zachtib on 2008-06-21
> **Mateo said:**
> Then it wouldn't be a pizza, would it?

Growing up allergic to cheese, I'd beg to differ :P

---

### Post by alwiap on 2008-06-21
the perfect pizza is a ******* hawaiian pizza (pineapple, ham, jalapeno, sometimes mushrooms)

no contest

---

### Post by Lostincyberspace on 2008-06-21
> **alwiap said:**
> the perfect pizza is a ******* hawaiian pizza (pineapple, ham, jalapeno, sometimes mushrooms)

no contest
You forgot spam!

---

### Post by bufsabre666 on 2008-06-21
the perfect pizza is a personalized issue, to me its a double cheese double pepperoni think crust, like they do it at wiseguys down the street here ((if youre ever in buffalo and want real pizza stop there, not joking, best pizza ever, and i grew up in nyc which is billed to have the best pizza))

---

### Post by init1 on 2008-06-21
```

mount /dev/mouth /body/face/mouth
mv /tmp/pizza /body/face/mouth

```

---

### Post by cardinals_fan on 2008-06-21
> **zachtib said:**
> Growing up allergic to cheese, I'd beg to differ :P
+1000000

I can't eat cheese.  It makes me sick.

---

### Post by zmjjmz on 2008-06-21
And I can't eat wheat/barley/rye/spelt. Or anything with gluten. Luckily there are gluten-free pizzas, but does Dominos make them?

---

### Post by cova on 2008-06-21
> **init1 said:**
> ```

mount /dev/mouth /body/face/mouth
mv /tmp/pizza /body/face/mouth

```

Haha. Ace.
Shame this wont do UK orders too. Feel like im missing out. Plus its only dominos to choose from and I know better places near where I live. Ah well... wheres the phone? Wonder if theyd understand me if I said "./pizzaparty -o -m -w -x 1 large thin"?

---

### Post by TBOL3 on 2008-06-22
Wait, they're on windows!

---

### Post by anemptygun on 2008-06-22
I officially have to try this!

---

### Post by aggiemarine07 on 2008-06-30
thanks for your help! I love this little program!



> **azurepancake said:**
> If your using Ubuntu Hardy, then the only package you need to install is libgetopt-mixed-perl..

```
sudo apt-get install libgetopt-mixed-perl
``` 

You can then run it straight from the directory..

```
./pizza_party
```

Or you can do what I did (and is recommended in the README) and move the "pizza_party" file to the '/usr/local/bin' directory..

```
sudo mv pizza_party /usr/local/bin
```

Then you can move the man file to the '/usr/local/man/man1' directory..

```
sudo mv man /usr/local/man/man1
```

Now you can just type..

```
pizza_party
``` 

..into the terminal to start the program. If you read the man page, you can create a configuration file called ".pizza_partyrc" in your /home/user directory. Here is the template..

```

       username=rtm
       password=simple
       default_quantity=3
       default_size=medium
       default_crust=deep
       default_toppings=pmx

```

Enjoy and have fun!

---

### Post by troy896 on 2008-06-30
could someone tell em what commands i shoudl put it if i have 7.10?

---

### Post by sharks on 2008-07-26
[http://www.linuxhaxor.net/2008/04/02/get-your-pizza-order-status-from-dominos-from-terminal/](http://www.linuxhaxor.net/2008/04/02/get-your-pizza-order-status-from-dominos-from-terminal/)

---

### Post by tiachopvutru on 2008-07-26
Imagine Linux users start ordering pizza from Domino just to try this script, and imagine Domino starts promoting Linux just because of that. :)

I'm kidding, of course.

---

### Post by adamogardner on 2008-07-27
this is so funny.  Domino's really sucks too.  but the idea of tracking your orders and mail packages and information in general through the terminal is awsome.

---

### Post by RiceMonster on 2008-07-27
I don't like Dominos, but that aside, this is way too geeky for me lol.

---

### Post by Kiefer Rodriguez on 2008-07-27
It starts with ordering a pizza, soon enough we'll all be making scripts to buy our groceries.. >_<
```

user@homenet$./wallmart.py

```

---

### Post by OutOfReach on 2008-07-27
I'd rather have Pizza Hut, but hey Dominos is still good :D :P

---

### Post by RiceMonster on 2008-07-27
> **Kiefer Rodriguez said:**
> It starts with ordering a pizza, soon enough we'll all be making scripts to buy our groceries.. >_<
```

user@homenet$./wallmart.py

```

You buy your groceries from wallmart? :-?

---

### Post by Kiefer Rodriguez on 2008-07-27
> **RiceMonster said:**
> You buy your groceries from wallmart? :-?

I buy mine at Woolworths :)
Everyone knows Wallmart :P

---

### Post by RiceMonster on 2008-07-27
Ok that makes sense then lol. That probably was the best choice because come to think of it, I don't know of any world wide chains other than Wallmart that sell groceries.

---

### Post by kko1 on 2008-07-27
> **Kiefer Rodriguez said:**
> Everyone knows Wallmart :P

> **RiceMonster said:**
> That probably was the best choice because come to think of it, I don't know of any world wide chains other than Wallmart that sell groceries.

[nitpick]
15 (16) countries is hardly worldwide. ;)
[/nitpick]

...though what Kiefer Rodriguez says isn't too far off, Walmart is notorious for their employee relations.

Ok back to pizza: Way too geeky yes, plus I prefer eating out. But cool anyway. :)

---

### Post by Mateo on 2008-07-27
There's also a program that can order pizza from the command line (i think it's Domino's too).  Someone should combine the features of both applications into one.

---

### Post by Diabolis on 2008-07-27
I wonder how real is this. How do they update the information, does the pizza has a microchip that tracks its status :shock:

---

### Post by Mateo on 2008-07-27
> **Diabolis said:**
> I wonder how real is this. How do they update the information, does the pizza has a microchip that tracks its status :shock:

Dominos tracks via their website.  This tool simply fools the website into thinking it is a web browser and retrieves the information.

---

### Post by D-EJ915 on 2008-07-27
> **Kiefer Rodriguez said:**
> I buy mine at Woolworths :)
Everyone knows Wallmart :P
nuke.py >> walmart.com

heh

pretty interesting dominio's thing, too much trouble but still hilarious

---

### Post by geogur on 2008-07-27
maybe linux would fix dominos to taste better . just like it made the internet better.

---

### Post by adamogardner on 2008-07-31
If we could track how our tax dollars are spent to subsidize Wal-mart (since quite often It can't sustain itself) from the CLI then I bet there would be fewer of them boxing dotting the country side.  

you might be on to something geogur.  Maybe our pizza (ie that of the linux user) can be open source.  We can collaborate on the different ingredients, new distros (pizzos?) hmmmm.

---

### Post by K.Mandla on 2008-07-31
> **sharks said:**
> [http://www.linuxhaxor.net/2008/04/02/get-your-pizza-order-status-from-dominos-from-terminal/](http://www.linuxhaxor.net/2008/04/02/get-your-pizza-order-status-from-dominos-from-terminal/)
Similar threads merged.

---

