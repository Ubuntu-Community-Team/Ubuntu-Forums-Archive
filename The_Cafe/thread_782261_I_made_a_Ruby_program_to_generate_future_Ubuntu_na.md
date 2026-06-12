---
title: "I made a Ruby program to generate future Ubuntu names"
date: 2008-05-04
forum: The Cafe
---

### Post by elmer_42 on 2008-05-04
I made a Ruby program that will generate names for the future Ubuntu releases up to 10.10. If somebody wants to expand it, feel free. The code is below, but here is some sample output:
```
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Inexorable Indosaurus
-- 9.04 --
Juggling Jackrabbit
-- 9.10 --
Knavish Katydid
-- 10.4 --
Laudable Lemming
-- 10.10 --
Massive Muskox
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Insightful Ingenia
-- 9.04 --
Juvenile Jackrabbit
-- 9.10 --
Kanny Kestrel
-- 10.4 --
Lofty Lizard
-- 10.10 --
Mysterious Monkey
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Incendiary Irritator
-- 9.04 --
Jodeling Jackalope
-- 9.10 --
Kinky Kingfisher
-- 10.4 --
Lofty Leech
-- 10.10 --
Muttering Mobutu
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Immodest Icebear
-- 9.04 --
Jolted Jackass
-- 9.10 --
Kinky Komodo
-- 10.4 --
Lofty Llama
-- 10.10 --
Moonlight Mobutu
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Innovatory Ingenia
-- 9.04 --
Jumping Jackass
-- 9.10 --
Kanny Koala
-- 10.4 --
Laughable Louse
-- 10.10 --
Malodorous Marten
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Incomparable Ingenia
-- 9.04 --
Jiggly Jubata
-- 9.10 --
Kanny Katydid
-- 10.4 --
Laudable Lemur
-- 10.10 --
Musical Mobutu
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Intimate Isopoda
-- 9.04 --
Jocular Joey
-- 9.10 --
Kleptomaniacal Kite
-- 10.4 --
Laughable Llama
-- 10.10 --
Moonlight Mantis
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Infallible Issasaurus
-- 9.04 --
Jolted Jackal
-- 9.10 --
Keen Kinkaju
-- 10.4 --
Leaping Liger
-- 10.10 --
Mighty Monkey
staylor@Mariner:~$ ruby names.rb 
-- 8.10 --
Ivory Iceweasel
-- 9.04 --
Jolly Junco
-- 9.10 --
Kurt Kingfisher
-- 10.4 --
Loquacious Labrador
-- 10.10 --
Mushy Macropod

```
```
ia = %w(Interstellar Icky Icy Idyllic Iffy Ignited Igneous Illuminating Illustrious Immodest Immortal Impressive Incendiary Incomparable Inconceivable Incontinent Incredible Incriminatory Indefatigable Industrious Indelible Inebriated Ineffable Inescapable Inestimable Inevitable Inexorable Infallible Inflammatory Inflationary Ingenious Ingratiating Initiatory Inky Impish Inner-city Innocent Innovatory Inquisitive Insanitary Insatiable Inscrutable Insightful Insolent Insouciant Inspired Inspirational Insurgent Intelligent Interagency Intercalary Intercessory Intercity Intermediary Intervarsity Intimate Intimidated Intrepid Inverted-snobbery Irate Iridescent Irie Irksome Irrefutable Itchy Itsy Investigatory Ivory)
ino = %w(Ibex Indri Ibis Icebear Iceweasel Ichtiosaurus Ichthyosaur Ifrit Iguana Impala Indri Insect Inkanyamba Imp Iguana Isopoda Irukandji Ivory Ichabodcraniosaurus Iguanodon Iguanoides Iguanosaurus Iliosuchus Ilokelesia Incisivosaurus Indosaurus Indosuchus Ingenia Inosaurus Irritator Isanosaurus Ischisaurus Ischyrosaurus Isisaurus Issasaurus Itemirus Iuticosaurus)
puts "-- 8.10 --"
puts ia[rand(ia.length)] + " " + ino[rand(ino.length)]
ja = %w(Jabbering Jaded Jaunty Jazzy Jealous Jiggly Jinchira Jittery Jiving Jocular Jocund Jodeling Joggling Jolly Jolted Jolty Jousing Jovial Joyous Jubilant Judicious Juggling Juicy Jumbled Jumping Jumpity Jungle Jurassic Juvenile)
jn = %w(Jacana Jackal Jackalope Jackass Jackrabbit Jaguar Javelina Jay Jellyfish Jerboa Joey Jubata Junco)
puts "-- 9.04 --"
puts ja[rand(ja.length)] + " " + jn[rand(jn.length)]
ka = %w(Kanny Keen Kicking Kicky Killer Kind Kingly Kinky Kleptomaniacal Knavish Knotty Kooky Kurt)
kn = %w(Kangaroo Katydid Kea Kestrel Kid Kingfisher Kinkaju Kite Kitten Kittyhawk Kiwi Knight Koala Komodo Kookaburra Kudu Kraut)
puts "-- 9.10 --"
puts ka[rand(ka.length)] + " " + kn[rand(kn.length)]
la = %w(Lampooning Languid Laughable Laughing Lazy Leaky Leaping Leapy Lethal Liberal Lively Lofty Lonely Loopy Loquacious Lordly Lucky Lugubrious Luscious Lusty Laudable)
ln = %w(Labrador Ladybug Lagomorph Lamb Lamprey Lark Leafhopper Leech Lemming Lemur Leopard Liger Limpet Lion Lizard Llama Loon Lorax Loris Louse Lynx Lobster)
puts "-- 10.4 --"
puts la[rand(la.length)] + " " + ln[rand(ln.length)]
ma = %w(Mad Magical Majestic Malicious Malodorous Mangy Manic Massive Masterful Melancholic Mellow Menacing Merry Mighty Mild Mistical Mushy Musky Musical Muttering Mysterious Mystic Moonlight) 
mn = %w(Macaw Macropod Magpie Mallard Marmot Manatee Mantis Marten Meadowlark Meerkat Millipede Mink Minnow Mobutu Mockingbird Mole Molly Mongoose Monkey Moose Mosquito Moth Motmot Mouse Muskrat Muskox Monitor Mule)
puts "-- 10.10 --"
puts ma[rand(ma.length)] + " " + mn[rand(mn.length)] 
```

---

### Post by zmjjmz on 2008-05-04
9.10 Kinky Kitten o.o

---

### Post by tamoneya on 2008-05-04
i think opera would be a little unhappy if we took kestrel since they are currently using that on their beta.

---

### Post by elmer_42 on 2008-05-04
I just grabbed all of these from [here]("https://wiki.ubuntu.com/DevelopmentCodeNames").

---

### Post by smoker on 2008-05-04
> -- 8.10 --
Incendiary Irritator

not sure this one will be adopted!
:-)

---

### Post by cardinals_fan on 2008-05-04
Moonlight Muskox!

---

### Post by tamoneya on 2008-05-04
it would be awesome if they actually used lemming on L.

---

### Post by Glaxed on 2008-05-04
LOL!
Nice one dude.

---

### Post by D-EJ915 on 2008-05-04
kleptomaniacal kite wins

---

### Post by swoll1980 on 2008-05-04
What does it use as a database?

---

### Post by Phenax on 2008-05-05
> **swoll1980 said:**
> What does it use as a database?

Manually defined arrays

---

### Post by elmer_42 on 2008-05-05
Yeah, sorry I didn't see your post, but it just uses names I copied from the Wiki and pasted into the program. I'm not *nearly* 1337 enough to make something that would get the names from the internet. Although, some people in Freenode on #ruby probably could.

---

