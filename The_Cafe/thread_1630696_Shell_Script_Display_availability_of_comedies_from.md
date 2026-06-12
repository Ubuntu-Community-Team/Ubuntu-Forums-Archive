---
title: "Shell Script: Display availability of comedies from blockbuster.com at local store"
date: 2010-11-22
forum: The Cafe
---

### Post by misha680 on 2010-11-22
This is quite silly, but blockbuster.com offers no way to get such a list.

Applations->Accessories->Terminal, type:
```

gedit /tmp/blockbuster.sh

```
Copy and paste the following into the window that appears:
```

#!/bin/bash
# Worked on Monday 11/22/2010
# ZIP code and xxx-xxxx blockbuster location hardcoded
# Retrieves status of all comedies from blockbuster.com (in stock, etc.) for given store
# Run with no parameters
# Ubuntu 10.10 Server amd64 running Lubuntu 10.10
ZIPCODE=77054 # !!! CHANGE ME
BLOCKBUSTERLOCATIONPHONE=666-9506 # !!! CHANGE ME
if [ $# == 0 ]; then
    date
    wget -qO- "http://www.blockbuster.com/browse/movieGenres/comedy?pg.1.page=1&pg.1.pageSize=10000&lc.1.viewType=list" > /tmp/movies
    echo "/browse/movieGenres/comedy" > /tmp/movies-extra
    grep Sub-categories /tmp/movies | sed 's/Filter Options.*//' | sed 's@<a href="\([^"]*\)"@/\n\1\n@g' | grep browse >> /tmp/movies-extra
    while read line; do
	bash $0 $line
    done < /tmp/movies-extra
    exit
else
    echo $1
    wget -qO- "http://www.blockbuster.com/$1?pg.1.page=1&pg.1.pageSize=10000&lc.1.viewType=list" > /tmp/movies-current
fi
grep '<span class="title">' /tmp/movies-current | sed 's@.*title="\([^"]*\)".*movieDetails/\([0-9]*\).*@\2 \1@' > /tmp/movies-processed
while read line; do
    TITLEID=`echo $line | sed 's/\([0-9]*\).*/\1/'`
    TITLE=`echo $line | sed 's/[0-9]* //'`
    wget -qO- --post-data="storeLocatorRequest.address.zipCode=$ZIPCODE&movieId=$TITLEID" http://www.blockbuster.com/browse/stores/storelocator/findStoresWithTitleAvailability > /tmp/movies-availability
    AVAILABILITY=`grep $BLOCKBUSTERLOCATIONPHONE /tmp/movies-availability | sed 's@.*</span>\(.*\)</span>.*@\1@'`
    echo $AVAILABILITY - $TITLE - $TITLEID
done < /tmp/movies-processed

```
Change the ZIPCODE and BLOCKBUSTERLOCATIONPHONE to the ZIP code and phone # of your local store, respectively (minus the area code, please follow my format or I can't promise it will work :( ).

File->Save. File->Quit.

Back to terminal:
```

bash /tmp/blockbuster.sh > /tmp/blockbuster 2>&1

```
Now wait (this will take a while). When it is done (go get coffee, take a walk, eat dinner, watch a movie, you get the hint).

Finally, to place the output in a friendly format type:
```

sort /tmp/blockbuster -u > /tmp/blockbuster.sorted
gedit /tmp/blockbuster.sorted &

```

Congratulations!!! If it worked, you should get something like this:
```

All copies are checked out - Because I Said So - 274938
All copies are checked out - Bride of Chucky - 129408
All copies are checked out - Diagnosis: Death - 461718
All copies are checked out - Evil Dead 2: Dead by Dawn - 10865
All copies are checked out - Extreme Movie - 289663
All copies are checked out - Freaky Friday - 12536
All copies are checked out - Life Is Beautiful - 116298
All copies are checked out - Like Mike - 209278
All copies are checked out - Must Love Dogs - 255948
All copies are checked out - Serious Moonlight - 439310
All copies are checked out - Something New - 265184
All copies are checked out - The Cable Guy - 93695
All copies are checked out - The Extra Man - 433946
All copies are checked out - Toy Story 2 - 135780
All copies are checked out - Woke Up Dead [Web Series] - 493353
/browse/movieGenres/comedy
/browse/movieGenres/comedy/caper
/browse/movieGenres/comedy/comedyDrama
/browse/movieGenres/comedy/comedyThriller
/browse/movieGenres/comedy/darkHumor
/browse/movieGenres/comedy/familyComedy
/browse/movieGenres/comedy/horrorComedy
/browse/movieGenres/comedy/militaryComedy
/browse/movieGenres/comedy/mockumentary
/browse/movieGenres/comedy/musicalComedy
/browse/movieGenres/comedy/romanticComedy
/browse/movieGenres/comedy/sci-FiComedy
/browse/movieGenres/comedy/screwballComedy
/browse/movieGenres/comedy/sexComedy
/browse/movieGenres/comedy/slapstick
/browse/movieGenres/comedy/spoof
/browse/movieGenres/comedy/sportsComedy
/browse/movieGenres/comedy/standupComedy
In stock - 11:14 - 230215
In stock - 13 Going on 30 - 228129
In stock - 17 Again - 371455
In stock - 1941 - 44
In stock - 2001 Maniacs: Field of Screams - 482852
In stock - 2:22 - 490596
In stock - 27 Dresses - 346788
In stock - 28 Days - 138963
In stock - 2 Days in Paris - 309374
In stock - 40 Days and 40 Nights - 205820
In stock - 44 Inch Chest - 429406
In stock - (500) Days of Summer - 402069
In stock - 7 Mujeres, 1 Homosexual y Carlos - 261808
In stock - About Schmidt - 211443
In stock - A Christmas Story - 40433
In stock - A Clockwork Orange - 6487
In stock - Adam Sandler's Eight Crazy Nights - 212895
In stock - Adaptation - 207186
In stock - A Day Without a Mexican - 247111
In stock - Addams Family Values - 81232
In stock - Adopted - 455681
In stock - Adventureland - 369039
In stock - After the Sunset - 235704
In stock - A Golden Christmas - 494808
In stock - A Good Year - 270285
In stock - Air Bud - 113248
In stock - Air Bud: Golden Receiver - 124103
In stock - Air Bud: Seventh Inning Fetch - 207850
In stock - Air Bud Spikes Back - 226059
In stock - Airplane! - 728
In stock - A League of Their Own - 20037
In stock - Alfie - 234949
In stock - Aliens in the Attic - 338116
In stock - All About Steve - 359659
In stock - All American Orgy - 476633
In stock - A Lot Like Love - 247642
In stock - Alvin and the Chipmunks - 338617
In stock - Alvin and the Chipmunks: The Squeakquel - 402654
In stock - Amélie - 191656
In stock - American Pie - 134926
In stock - American Pie 2 - 197018
In stock - American Pie Presents: The Book of Love - 468109
In stock - American Pie Presents: The Naked Mile - 327179
In stock - American Psycho - 138924
In stock - Amor Letra por Letra - 424846
In stock - An American Carol - 392860
In stock - An American Werewolf in London - 1209
In stock - Annie - 1475
In stock - Another Cinderella Story - 405441
In stock - Aquamarine - 262432
In stock - Armored - 381381
In stock - Army of Darkness - 1669
In stock - A Serious Man - 348966
In stock - Assassination of a High School President - 358672
In stock - Austin Powers in Goldmember - 209722
In stock - Austin Powers: The Spy Who Shagged Me - 134706
In stock - Away We Go - 390183
In stock - Baby on Board - 439960
In stock - Baby's Day Out - 89700
In stock - Balls of Fury - 273926
In stock - Balls Out: Gary the Tennis Coach - 327003
In stock - Bandslam - 389004
In stock - Bedtime Stories - 340920
In stock - Bee Movie - 264082
In stock - Beerfest - 280241
In stock - Beethoven - 2673
In stock - Beethoven's 2nd - 81230
In stock - Beethoven's 3rd - 150355
In stock - Beethoven's 4th - 197486
In stock - Beetlejuice - 2703
In stock - Be Kind Rewind - 284674
In stock - Bend It Like Beckham - 220773
In stock - Best in Show - 162409
In stock - Beverly Hills Chihuahua - 356279
In stock - Bewitched - 236981
In stock - Bicentennial Man - 135915
In stock - Big Fat Liar - 206207
In stock - Big Fish - 232143
In stock - Big Momma's House - 141448
In stock - Big Momma's House 2 - 262668
In stock - Black Knight - 203007
In stock - Black Sheep - 310372
In stock - Blades of Glory - 276880
In stock - Blazing Saddles - 3628
In stock - Bob the Butler - 259106
In stock - Borat - 282014
In stock - Bored to Death: Season 01 - 486510
In stock - Bottle Shock - 387722
In stock - Bride Wars - 386145
In stock - Brief Interviews With Hideous Men - 353344
In stock - Bring It On - 152279
In stock - Bring It On Again - 238100
In stock - Bring It On: All or Nothing - 286453
In stock - Broken Embraces - 386603
In stock - Bruce Almighty - 221707
In stock - Brüno - 329275
In stock - Burn After Reading - 328582
In stock - Buzz Lightyear of Star Command: The Adventure Begins - 159465
In stock - Cabin Fever 2: Spring Fever - 342504
In stock - Cake - 257233
In stock - Camille - 386008
In stock - Can't Buy Me Love - 5089
In stock - Cars - 232197
In stock - Casanova - 253214
In stock - Cash - 403332
In stock - Casper - 92299
In stock - Catch-22 - 5487
In stock - Catch and Release - 266510
In stock - Catch That Kid - 224742
In stock - Cats & Dogs - 193772
In stock - Cats & Dogs: The Revenge of Kitty Galore - 413450
In stock - Cemetery Junction - 453634
In stock - Chaos Theory - 272174
In stock - Charlie Bartlett - 288731
In stock - Chasing Amy - 110964
In stock - Cheaper by the Dozen 2 - 264859
In stock - Cheaper by the Dozen - 228172
In stock - Chicken Little - 243320
In stock - Chocolate Sundaes Comedy Show: Live on Sunset Strip! - 478555
In stock - Choke - 362553
In stock - Chris Rock: Kill the Messenger - 423695
In stock - Christmas Do-Over - 333854
In stock - Christmas With the Kranks - 240809
In stock - Chuck: Season 01 - 376213
In stock - City Island - 442535
In stock - Click - 270881
In stock - Clockstoppers - 206638
In stock - Cloudy with a Chance of Meatballs - 427665
In stock - Clue - 6531
In stock - Code Name: The Cleaner - 265615
In stock - Cold Souls - 430453
In stock - College Road Trip - 356280
In stock - Comedian - 212081
In stock - Conversations With Other Women - 271842
In stock - Cop Out - 438374
In stock - Cougar Club - 370103
In stock - Couples Retreat - 423080
In stock - Daddy Day Camp - 340814
In stock - Dane Cook's Tourgasm [TV Series] - 287909
In stock - Dan in Real Life - 272007
In stock - Date for Hire - 490995
In stock - Date Movie - 272138
In stock - Date Night - 420695
In stock - Dazed and Confused - 82485
In stock - Dead Snow - 431897
In stock - Death at a Funeral - 284336
In stock - Death at a Funeral - 427605
In stock - Deck the Halls - 284706
In stock - Dedication - 275679
In stock - Definitely, Maybe - 307684
In stock - Delta Farce - 288732
In stock - Deuce Bigalow: European Gigolo - 237433
In stock - Diary of a Wimpy Kid - 444061
In stock - Did You Hear About the Morgans? - 427445
In stock - Disaster Movie - 400121
In stock - Disney's The Kid - 143206
In stock - Dodgeball: A True Underdog Story - 232136
In stock - Don't Look Down - 397751
In stock - Double, Double, Toil & Trouble - 164606
In stock - Drag Me to Hell - 387307
In stock - DragonBall Z: Bojack Unbound - 253056
In stock - Dr. Dolittle: Million Dollar Mutts - 439239
In stock - Dr. Dolittle: Tail to the Chief - 386279
In stock - Dumb and Dumberer: When Harry Met Lloyd - 223001
In stock - Duplex - 220130
In stock - Duplicity - 382354
In stock - DysFunKtional Family - 219519
In stock - Easy Virtue - 388911
In stock - Eddie Murphy: Delirious - 10208
In stock - Eddie Murphy: Raw - 10209
In stock - Edward Scissorhands - 10253
In stock - Elf - 228169
In stock - Elizabethtown - 230619
In stock - Ella Enchanted - 225256
In stock - Employee of the Month - 275638
In stock - Enchanted - 275538
In stock - Entrapment - 132660
In stock - Envy - 223717
In stock - Epic Movie - 327153
In stock - Eurotrip - 237750
In stock - Evan Almighty - 271251
In stock - Everybody Wants to Be Italian - 279537
In stock - Evolution - 191873
In stock - Failure to Launch - 267504
In stock - Family Guy: Blue Harvest - 383874
In stock - Family Guy: Partial Terms of Endearment - 492374
In stock - Fantastic Mr. Fox - 328348
In stock - Fargo - 93335
In stock - Fast Food Nation - 264590
In stock - Fast Times at Ridgemont High - 11309
In stock - Fat Albert - 231383
In stock - Feast - 265774
In stock - Fido - 269416
In stock - Fight Club - 135424
In stock - Finding Bliss - 434760
In stock - Fired Up! - 399476
In stock - First Sunday - 340095
In stock - Flawless - 364933
In stock - Flirting with Forty - 436314
In stock - Flubber - 115052
In stock - Forgetting Sarah Marshall - 356273
In stock - Forrest Gump - 89704
In stock - Freaky Friday - 225255
In stock - Fred Claus - 280967
In stock - Fred: The Movie - 494359
In stock - French Film - 431960
In stock - Friends With Money - 259624
In stock - Funny People - 394648
In stock - Furry Vengeance - 434799
In stock - Futurama: Bender's Big Score - 367884
In stock - Futurama: Bender's Game - 419066
In stock - Futurama: Into the Wild Green Yonder - 425374
In stock - Galaxy Quest - 135902
In stock - Garden State - 241803
In stock - Garfield Gets Real - 370110
In stock - Garfield's FunFest - 417311
In stock - Garfield: The Movie - 228339
In stock - George Lopez: Tall, Dark & Chicano - 456906
In stock - George of the Jungle - 113214
In stock - George of the Jungle 2 - 225716
In stock - Georgia Rule - 307801
In stock - Get Him to the Greek - 400544
In stock - Get Smart - 310795
In stock - Getting There: Sweet 16 and Licensed to Drive - 209991
In stock - Ghostbusters - 13357
In stock - Ghosts of Girlfriends Past - 289214
In stock - Ghost Town - 346007
In stock - Gigantic - 393553
In stock - Gone In 60 Seconds - 141097
In stock - Good Boy! - 223062
In stock - Good Burger - 113237
In stock - Good Luck Chuck - 288613
In stock - Greenberg - 430755
In stock - Gremlins - 14355
In stock - Grown Ups - 436256
In stock - Hairspray - 14589
In stock - Hairspray - 268745
In stock - Hamlet 2 - 371929
In stock - Hannah Montana: The Movie - 392918
In stock - Happy Feet - 261537
In stock - Happy Gilmore - 93643
In stock - Happy-Go-Lucky - 389408
In stock - Harsh Times - 258212
In stock - Heathers - 15105
In stock - Henry Poole is Here - 351656
In stock - Herbie: Fully Loaded - 244198
In stock - He's Just Not That Into You - 346455
In stock - Hey Hey It's Esther Blueburger - 285604
In stock - High Fidelity - 138975
In stock - High School Musical 2 - 341892
In stock - High School Musical - 281657
In stock - High School Musical 3: Senior Year - 340921
In stock - History of the World -- Part I - 15620
In stock - Hitch - 240816
In stock - Holiday Inn - 15709
In stock - Holiday in the Sun - 202286
In stock - Home Alone - 15827
In stock - Home Alone 2: Lost in New York - 15828
In stock - Home Alone 3 - 115056
In stock - Home Alone 4: Taking Back the House - 220576
In stock - Honey, We Shrunk Ourselves - 134134
In stock - Hostel Part II - 288670
In stock - Hotel for Dogs - 372278
In stock - Hot Rod - 305423
In stock - Hot Shots! Part Deux - 16079
In stock - Hot Tub Time Machine - 437485
In stock - Howard the Duck - 16333
In stock - How the Garcia Girls Spent Their Summer - 258153
In stock - How to Eat Fried Worms - 270759
In stock - I Am a Sex Addict - 263221
In stock - Ice Princess - 247109
In stock - I Could Never Be Your Woman - 270673
In stock - Idiocracy - 248357
In stock - I Do & I Don't - 471167
In stock - Igor - 306658
In stock - I Hate Valentine's Day - 441341
In stock - I Hope They Serve Beer in Hell - 449740
In stock - I Love You, Beth Cooper - 352852
In stock - Imagine That - 340414
In stock - I'm Gonna Git You Sucka! - 16656
In stock - In Bruges - 336525
In stock - Infestation - 401837
In stock - Inspector Gadget - 134932
In stock - Intolerable Cruelty - 225397
In stock - Into the Blue - 243319
In stock - I Sell the Dead - 434748
In stock - It Happened One Night - 17613
In stock - I Think I Love My Wife - 287621
In stock - It's Complicated - 402075
In stock - Jam - 273028
In stock - Jamie Foxx Unleashed: Lost, Stolen and Leaked! - 221582
In stock - Jennifer's Body - 383756
In stock - Jerry Maguire - 94098
In stock - Jimmy Neutron: Boy Genius - 203702
In stock - Julie & Julia - 382351
In stock - Jungle 2 Jungle - 111084
In stock - Juno - 307406
In stock - Just for Laughs: Stand Up, Vol. 2 - On the Edge - 276230
In stock - Just Friends - 255259
In stock - Just Like Heaven - 259798
In stock - Just My Luck - 264941
In stock - Just Wright - 474090
In stock - Katt Williams: It's Pimpin' Pimpin' - 420881
In stock - Katt Williams: Katthouse Comedy - 426636
In stock - Katt Williams: The Pimp Chronicles, Part 1 - 311829
In stock - Kevin Hart: Seriously Funny - 483615
In stock - Kicking & Screaming - 246170
In stock - Killers - 436959
In stock - King of California - 286218
In stock - Kit Kittredge: An American Girl - 349910
In stock - Knocked Up - 283664
In stock - Knucklehead - 484693
In stock - Kung Fu Hustle - 254538
In stock - Kung Fu Panda - 305077
In stock - Kung Pow! Enter the Fist - 205976
In stock - Labor Pains - 404870
In stock - La Dolce Vita - 19495
In stock - Ladron Que Roba a Ladron - 345868
In stock - La Fille Coupée en Deux - 370934
In stock - Lagaan: Once Upon a Time In India - 197905
In stock - Lars and the Real Girl - 288733
In stock - Leap Year - 429818
In stock - Leatherheads - 323174
In stock - Leaves of Grass - 386093
In stock - Legend of the Bog - 429117
In stock - Lemony Snicket's A Series of Unfortunate Events - 228915
In stock - Leprechaun: Back 2 tha Hood - 234894
In stock - Letters to Juliet - 450574
In stock - License to Wed - 286294
In stock - Life-Size - 173906
In stock - Lilo & Stitch - 209171
In stock - Little Children - 264212
In stock - Little Giants - 91087
In stock - Little Miss Sunshine - 271419
In stock - Little Nicky - 166358
In stock - Live! - 344644
In stock - Lock, Stock and Two Smoking Barrels - 124122
In stock - Lottery Ticket - 456952
In stock - Love and Other Disasters - 264706
In stock - Love Stinks - 135429
In stock - Lucky Number Slevin - 260047
In stock - MacGruber - 452922
In stock - Madagascar - 231975
In stock - Madagascar: Escape 2 Africa - 272006
In stock - Made of Honor - 333733
In stock - Mad Money - 261805
In stock - Major Payne - 92153
In stock - Mamma Mia! - 336676
In stock - Management - 365665
In stock - Mañana te Cuento - 287190
In stock - Man on the Moon - 135286
In stock - Margot at the Wedding - 288898
In stock - Marie and Bruce - 229610
In stock - Marley & Me - 367201
In stock - Marmaduke - 456950
In stock - Married Life - 326446
In stock - Martian Child - 264054
In stock - Mary Poppins - 22125
In stock - M*A*S*H - 42077
In stock - Matchstick Men - 225259
In stock - Matilda - 93956
In stock - Me and You and Everyone We Know - 252831
In stock - Meet Bill - 287620
In stock - Meet Dave - 327150
In stock - Meet the Spartans - 382112
In stock - Mel Brooks Box Set Collection [8 Discs] - 304190
In stock - Men in Black - 111322
In stock - Men in Black II - 207183
In stock - Me & Orson Welles - 390651
In stock - Middle of Nowhere - 405446
In stock - Midgets vs. Mascots - 442485
In stock - Mike Epps: Funny Bidness - 433598
In stock - Mike Epps: Live From Club Nokia - 489771
In stock - MILF - 494096
In stock - Mini's First Time - 263601
In stock - Miss March - 405664
In stock - Miss Pettigrew Lives for a Day - 341941
In stock - Monkey Trouble - 90686
In stock - Monster-in-Law - 235482
In stock - Monsters, Inc. - 202608
In stock - Monsters vs. Aliens - 329889
In stock - Mr. Bean's Holiday - 287613
In stock - Mr. Magorium's Wonder Emporium - 264198
In stock - Mr. Woodcock - 263420
In stock - Muppets from Space - 134928
In stock - Music and Lyrics - 279096
In stock - MXP: Most Xtreme Primate - 228164
In stock - My Best Friend's Girl - 361372
In stock - My Life in Ruins - 417280
In stock - My Name Is Bruce - 310369
In stock - My Super Ex-Girlfriend - 269242
In stock - Nacho Libre - 271637
In stock - Nanny McPhee - 245780
In stock - National Lampoon's Animal House - 39877
In stock - National Lampoon's Christmas Vacation - 81338
In stock - National Lampoon's Dorm Daze 2 - 285225
In stock - National Lampoon's Gold Diggers - 253515
In stock - National Lampoon's Spring Break - 336499
In stock - National Lampoon's Van Wilder: The Rise of Taj - 281682
In stock - National Treasure - 231200
In stock - National Treasure: Book of Secrets - 329822
In stock - Nativity - 463241
In stock - New in Town - 370556
In stock - New York, I Love You - 399189
In stock - Nick and Norah's Infinite Playlist - 375884
In stock - Nobel Son - 345385
In stock - Norbit - 271925
In stock - No Reservations - 279032
In stock - Nothing But Trouble - 25152
In stock - Observe and Report - 394281
In stock - Ocean's Eleven - 203009
In stock - Ocean's Thirteen - 282317
In stock - Ocean's Twelve - 231313
In stock - Office Space - 131354
In stock - O'Horten - 403638
In stock - Old Dogs - 349304
In stock - One Flew Over the Cuckoo's Nest - 25593
In stock - Open Season - 245777
In stock - Operation: Endgame - 482814
In stock - Original Latin Kings of Comedy - 231887
In stock - Osmosis Jones - 197019
In stock - Our Family Wedding - 456467
In stock - Out Cold - 203008
In stock - Over Her Dead Body - 307407
In stock - Over the Hedge - 231976
In stock - Paper Heart - 429824
In stock - Paul Blart: Mall Cop - 374336
In stock - Pee-Wee's Big Adventure - 26476
In stock - Penelope - 269716
In stock - Picture Perfect - 113179
In stock - PiGS - 363094
In stock - Piranha - 26921
In stock - Pirate Radio - 394127
In stock - Platinum Comedy Series: Cedric the Entertainer - Starting Lineup 2 - 230668
In stock - Please Give - 475688
In stock - Pokemon: Mewtwo Returns - 204783
In stock - Police Academy - 27139
In stock - Porky's - 27236
In stock - Post Grad - 417973
In stock - Practical Magic - 129409
In stock - Pride & Prejudice - 250396
In stock - Prime - 255429
In stock - Private Valentine: Blonde and Dangerous - 355566
In stock - Ramona and Beezus - 372893
In stock - Ratatouille - 281214
In stock - Rat Race - 196601
In stock - Reno 911!: Miami - 281669
In stock - Rent a Car - 485029
In stock - Return to Sleepaway Camp - 234989
In stock - Richard Pryor: Here and Now - 29009
In stock - Richard Pryor: Live on the Sunset Strip - 42949
In stock - Risky Business - 29182
In stock - Robots - 231534
In stock - RocknRolla - 352130
In stock - Ron White: They Call Me - 246984
In stock - Rookie of the Year - 29616
In stock - Rudo y Cursi - 359125
In stock - Rumor Has It... - 254120
In stock - Runaway Bride - 134937
In stock - Run, Fat Boy, Run - 308359
In stock - Running With Scissors - 260742
In stock - RV - 262467
In stock - Saint John of Las Vegas - 452169
In stock - Santa Baby - 351303
In stock - Scary Movie - 135934
In stock - Scary Movie 2 - 193771
In stock - Scary Movie 3 - 225347
In stock - Scary Movie 4 - 229129
In stock - School of Rock - 223748
In stock - Scooby-Doo - 207082
In stock - Scooby-Doo 2: Monsters Unleashed - 228761
In stock - Scooby-Doo!: Abracadabra-Doo - 469603
In stock - Scooby-Doo!: The Mystery Begins - 452561
In stock - Scoop - 283945
In stock - Scott Pilgrim vs. the World - 396130
In stock - Scrooged - 30477
In stock - S. Darko - 402179
In stock - Secondhand Lions - 226037
In stock - Secretary - 207943
In stock - See **** Run - 444434
In stock - Seeing Other People - 246048
In stock - See No Evil, Hear No Evil - 30725
In stock - Semi-Pro - 328271
In stock - Sex and Death 101 - 326798
In stock - Sex and the City 2 - 428779
In stock - Sex and the City - 361248
In stock - Sex and the City: Season 02 - 230641
In stock - Sex and the City: Season 03 - 230642
In stock - Sex and the City: Season 04 - 230643
In stock - Sex and the City: Season 05 - 230644
In stock - Sex Drive - 383287
In stock - Shallow Hal - 202613
In stock - Shampoo - 31045
In stock - Shaolin Soccer - 202393
In stock - Shaq and Cedric the Entertainer Present: All Star Comedy Jam - 450187
In stock - Shaquille O'Neal Presents: All Star Comedy Jam - Live from Dallas - 493097
In stock - Shaquille O'Neal Presents: All Star Comedy Jam - Live from South Beach - 469938
In stock - Shark Tale - 228908
In stock - Shaun of the Dead - 241894
In stock - She Hate Me - 242641
In stock - She's Out of My League - 452724
In stock - She's the Man - 270592
In stock - Shorts - 404316
In stock - Shrek 2 - 228904
In stock - Shrek the Third - 261088
In stock - Shrink - 431856
In stock - Sideways - 237431
In stock - Sky High - 253514
In stock - Sliding Doors - 116385
In stock - Smart People - 311958
In stock - Smother - 325107
In stock - Snakes on a Plane - 253809
In stock - Snatch - 172807
In stock - Snow Dogs - 205977
In stock - Soccer Dog: European Cup - 247887
In stock - Solitary Man - 422507
In stock - Solo Quiero Caminar - 429091
In stock - Son of Rambow - 333497
In stock - Soul Plane - 232008
In stock - Southland Tales - 264148
In stock - South Park: Bigger, Longer & Uncut - 134922
In stock - Space Chimps - 283679
In stock - Space Jam - 94014
In stock - Spread - 392235
In stock - Spun - 211958
In stock - Spy Kids 2: The Island of Lost Dreams - 209941
In stock - Spy Kids 3-D: Game Over - 223718
In stock - Step Brothers - 308624
In stock - Steppin - 422163
In stock - Stranger Than Fiction - 260485
In stock - Strike - 282316
In stock - Stripes - 33483
In stock - Stripper Academy - 428498
In stock - Stuart Little - 135903
In stock - Sunshine Cleaning - 326940
In stock - Superbad - 306051
In stock - Surf's Up - 256345
In stock - Surrogates - 344494
In stock - Sweeney Todd: The Demon Barber of Fleet Street - 288350
In stock - Switching Goals - 155289
In stock - Swordfish - 191874
In stock - Taking Woodstock - 400458
In stock - Talk to Me - 285157
In stock - Talladega Nights: The Ballad of Ricky Bobby - 262431
In stock - Team America: World Police - 249622
In stock - Teeth - 333465
In stock - Tenacious D in the Pick of Destiny - 265612
In stock - Terry Fator: Live from Las Vegas - 451284
In stock - That Darn Cat - 111007
In stock - The 40-Year-Old Virgin - 258395
In stock - The 41-Year-Old Virgin Who Knocked Up Sarah Marshall and Felt Superbad About It - 477091
In stock - The Addams Family - 410
In stock - The American Mall - 401044
In stock - The Ant Bully - 269713
In stock - The Apple Dumpling Gang - 1566
In stock - The Apple Dumpling Gang Rides Again - 1567
In stock - The Aristocrats - 258842
In stock - The Babysitters - 371434
In stock - The Back-up Plan - 449848
In stock - The Bad News Bears - 256550
In stock - The Bank Job - 340675
In stock - The Benchwarmers - 261877
In stock - The Big Green - 93296
In stock - The Big Lebowski - 115093
In stock - The Blind Side - 436895
In stock - The Bounty Hunter - 467061
In stock - The Break-Up - 262067
In stock - The Bucket List - 289757
In stock - The 'Burbs - 4826
In stock - The Chosen One - 495463
In stock - The Chumscrubber - 248070
In stock - The Code - 375016
In stock - The Devil Wears Prada - 272172
In stock - The Ex - 266870
In stock - The Family Stone - 261802
In stock - The Foot Fist Way - 282819
In stock - The Game Plan - 323073
In stock - The Girl Next Door - 232166
In stock - The Good Night - 275489
In stock - The Good Student - 426358
In stock - The Goonies - 13920
In stock - The Great Buck Howard - 287551
In stock - The Great Outdoors - 14218
In stock - The Groomsmen - 265096
In stock - The Heartbreak Kid - 292718
In stock - The Hitchhiker's Guide to the Galaxy - 237056
In stock - The Holiday - 278530
In stock - The Hot Chick - 216167
In stock - The House Bunny - 369628
In stock - The Ice Harvest - 245656
In stock - The Informant! - 397234
In stock - The Informers - 323176
In stock - The Invention of Lying - 371099
In stock - The Italian Job - 222955
In stock - The Jane Austen Book Club - 330338
In stock - The Joneses - 461122
In stock - The Kids Are All Right - 475846
In stock - The Ladies Man - 166354
In stock - The Ladykillers - 230635
In stock - The Last Airbender - 336357
In stock - The Last Day of Summer - 355611
In stock - The Last Kiss - 260753
In stock - The Last Word - 386179
In stock - The Lizzie McGuire Movie - 220702
In stock - The Longest Yard - 248545
In stock - The Longshots - 368949
In stock - The Lookout - 270527
In stock - The Love Guru - 340817
In stock - The Man with One Red Shoe - 21819
In stock - The Men Who Stare at Goats - 419780
In stock - The Money Pit - 23164
In stock - The Muppets Take Manhattan - 23675
In stock - The Nanny Diaries - 283280
In stock - Then She Found Me - 265097
In stock - The Office: Season 02 - 266332
In stock - The Office: Season 03 - 311267
In stock - The Office: Season 04 - 360002
In stock - The Office: Season 05 - 423613
In stock - The Onion Movie - 245799
In stock - The Other End of the Line - 412743
In stock - The Pacifier - 248356
In stock - The People Under the Stairs - 26518
In stock - The Perfect Holiday - 323074
In stock - The Philadelphia Story - 26769
In stock - The Pink Panther 2 - 308371
In stock - The Pink Panther - 243254
In stock - The Prince and the Pauper: The Movie - 369480
In stock - The Princess Diaries - 196604
In stock - The Private Lives of Pippa Lee - 381357
In stock - The Producers - 255407
In stock - The Proposal - 354780
In stock - There's Something About Mary - 119118
In stock - The Revenge of the Pink Panther - 28935
In stock - The Ringer - 237151
In stock - The Rocker - 352854
In stock - The Royal Tenenbaums - 202718
In stock - The Sandlot 2 - 259784
In stock - The Sandlot - 30137
In stock - The Sandlot: Heading Home - 340992
In stock - The Santa Clause 2 - 212652
In stock - The Santa Clause 3: The Escape Clause - 262465
In stock - The Santa Clause - 91541
In stock - The Score - 194142
In stock - The Shaggy Dog - 253560
In stock - The Simpsons Movie - 282195
In stock - The Sisterhood of the Traveling Pants 2 - 356089
In stock - The Sisterhood of the Traveling Pants - 248624
In stock - The Six Wives of Henry Lefay - 365773
In stock - The Slammin' Salmon - 382355
In stock - The SpongeBob SquarePants Movie - 225340
In stock - The Sweetest Thing - 206647
In stock - The Taking of Pelham 1 2 3 - 373938
In stock - The Ugly Truth - 384271
In stock - The Visitor - 311816
In stock - The Wackness - 368805
In stock - The Waterboy - 129519
In stock - The Wedding Date - 236704
In stock - The Wild - 266118
In stock - The Witches of Eastwick - 38829
In stock - The Women - 354068
In stock - This Is Spinal Tap - 34999
In stock - This Thing of Ours - 229434
In stock - Three Can Play That Game - 385832
In stock - Three Kings - 135626
In stock - Thunderpants - 211273
In stock - Tim Burton's Corpse Bride - 235295
In stock - To Die For - 92360
In stock - Tommy Boy - 92182
In stock - Tooth Fairy - 393521
In stock - Toy Story 3 - 340672
In stock - Trailer Park Boys: The Movie - 264527
In stock - Triangle - 353284
In stock - Trust the Man - 257518
In stock - Two Can Play That Game - 198921
In stock - Two Weeks - 329890
In stock - Tyler Perry's Daddy's Little Girls - 309395
In stock - Tyler Perry's Diary of a Mad Black Woman - 260486
In stock - Tyler Perry's Madea Goes to Jail - 399586
In stock - Tyler Perry's Madea's Family Reunion - 261538
In stock - Tyler Perry's Meet the Browns - 355098
In stock - Tyler Perry's Why Did I Get Married? - 342468
In stock - Tyler Perry's Why Did I Get Married Too? - 438874
In stock - Unstable Fables: 3 Pigs and a Baby - 389189
In stock - Up in the Air - 403516
In stock - Valentine's Day - 450716
In stock - Vampire Killers - 425535
In stock - Van Wilder: Freshman Year - 431095
In stock - Volver - 264458
In stock - Waitress - 270549
In stock - Waking Ned Devine - 129371
In stock - Walk Hard: The Dewey Cox Story - 309104
In stock - Wallace & Gromit: The Curse of the Were-Rabbit - 232314
In stock - Wanda Sykes: I'ma Be Me - 468886
In stock - Wanda Sykes: Sick & Tired - 307622
In stock - War, Inc. - 327475
In stock - Wedding Crashers - 243317
In stock - Whatever Works - 417894
In stock - What Happens in Vegas - 353192
In stock - What Just Happened - 288903
In stock - When in Rome - 391665
In stock - Whip It - 389549
In stock - Will Ferrell: You're Welcome, America: A Final Night With George W. Bush - 439814
In stock - Women in Trouble - 432779
In stock - Wonder Boys - 137026
In stock - Working Girl - 39055
In stock - World's Greatest Dad - 416560
In stock - Wristcutters: A Love Story - 276291
In stock - Year One - 354401
In stock - Young Frankenstein - 39537
In stock - Yours, Mine & Ours - 264196
In stock - Y Tu Mamá También - 197936
In stock - Zack and Miri Make a Porno - 381514
In stock - Zombieland - 421419
In stock - Zombie Strippers - 386095
Not carried at this location - 100 Ways to Murder Your Wife - 223660
...

```
Not carried at this location entries will be at the bottom, so you can ignore those :)

Misha

---

