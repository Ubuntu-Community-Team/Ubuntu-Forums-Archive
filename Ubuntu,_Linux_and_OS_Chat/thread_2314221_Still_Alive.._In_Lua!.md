---
title: "Still Alive.. In Lua!"
date: 2016-02-19
forum: Ubuntu, Linux and OS Chat
---

### Post by constantine7 on 2016-02-19
Hey everyone, forgive this being my first post but I wanted to share with you all something I just created in Lua. I haven't found this done anywhere, at least to my best knowledge not done completely.
I've tried my best to recreate Portal 'Still Alive' in Lua. I used my best effort to get the timing right and everything so it matches up with the song.
It's now my screensaver ;)

Here it is!

[B]Also, for some reason terminal doesn't show the 'typing'. 
If you want to see it working in full try it here: [https://repl.it/BoU3/0](https://repl.it/BoU3/0)[URL="https://repl.it/BoU1/0"]

[/URL][/B]Original: [https://www.youtube.com/watch?v=Y6ljFaKRTrI](https://www.youtube.com/watch?v=Y6ljFaKRTrI)

```
local clock = os.clock
function sleep(n)  -- seconds
  local t0 = clock()
  while clock() - t0 <= n do end
end
function write(x)
    for i = 1, #x do
        local c = x:sub(i,i)
        io.write(c)
        sleep(0.07)
    end
end
function delay(v)
    if v == 's' then
        sleep(1)
        print(' ')
    elseif v == 'ss' then
        sleep(0.5)
        print(' ')
    elseif v == 'sss' then
        sleep(0.32)
        print(' ')
    elseif v == 'm' then
        sleep(2)
        print(' ')
    elseif v == 'b' then
        sleep(2.8)
        print(' ')
    end
end
--Created by devhotissue.tumblr.com
--Portal <3------------------------
--STILL ALIVE----------------------
--LUA VERSION----------------------
write("This was a triumpth. ")
delay('s')
write("I'm making a note here: ")
delay('ss')
write("HUGE SUCCESS. ")
delay('m')
write('It\'s hard to overstate ')
delay('ss')
write('my satisfaction. ')
delay('b')
print('                .,-:;//;:=,                  ')
print('            . :H@@@MM@M#H/.,+%;,             ')
print('         ,/X+ +M@@M@MM%=,-%HMMM@X/,          ')
print('       -+@MM; #M@@MH+-,;XMMMM@MMMM@+-        ')
print('      ;@M@@M- XM@X;. -+XXXXXHHH@M@M#@/.      ')
print('    ,%MM@@MH ,@%=            .---=-=:=,.     ')
print('    =@#@@@MX .,              -%HX##%%%+;     ')
print('   =-./@M@M$                  .;@MMMM@MM:    ')
print('   X@/ -#MM/                    .+MM@@@M$    ')
print('  ,@M@H: :@:                    . =X#@@@@-   ')
print('  ,@@@MMX, .                    /H- ;@M@M=   ')
print('  .H@@@@M@+,                    %MM+..%#$.   ')
print('   /MMMM@MMH/.                  XM@MH; =;    ')
print('    /%+%#XHH@$=              , .H@@@@MX,     ')
print('     .=--------.           -%H.,@@@@@MX,     ')
print('     .%MM@@@HHHXX###%+= .:#MMX =M@@MM%.      ')
print('       =XMMM@MM@MM#H;,-+HMM@M+ /MMMX=        ')
print('         =%@M@M#@$-.=#@MM@@@M; %M%=          ')
print('           ,:+$+-,/H#MMMMMMM@= =,            ')
print('                 =++%%%%+/:-.                ')
print('')
sleep(0.9)
write('Aperature Science ')
delay('m')
write('We do what we must')
delay('s')
write('because we can. ')
delay('m')
write('For the good of all of us. ')
delay('s')
write('Except the ones who are dead ')
print('')
delay('s')
write('But there\'s no sense crying ')
print('')
write('over every mistake.')
delay('ss')
write('You just keep on trying ')
print('')
write('till you run out of cake. ')
delay('s')
write('And the science gets done. ')
delay('ss')
write('And you make a neat gun. ')
delay('ss')
write('For the people who are ')
delay('ss')
write('still alive. ')
for i = 1, 255 do
    print()
end
write('Dear <<Subject Name Here>>, ')
print()
delay('b')
write('I\'m not even angry. ')
delay('m')
write('I\'m being so sincere ')
sleep(0.4)
write('right now. ')
delay('b')
write('Even ')
sleep(0.4)
write('though ')
sleep(0.2)
write('you broke my heart. ')
delay('s')
write('And killed me. ')
delay('b')
write('And tore me to pieces. ')
delay('m')
write('And threw every piece')
sleep(0.5)
write(' into')
sleep(0.2)
write(' a fire. ')
delay('b')
write('As they burned it hurt because')
delay('ss')
write('I was so happy for you! ')
delay('ss')
write('Now these points of data')
delay('sss')
write('make a beautiful line. ')
delay('sss')
write('And we\'re out of beta. ')
delay('sss')
write('We\'re releasing on time. ')
delay('s')
write('So I\'m GLaD. I got burned. ')
delay('ss')
write('Think of all the things we learned')
delay('sss')
write('for the people who are ')
delay('s')
write('still alive.')
for i = 1, 255 do
    print()
end
sleep(2)
write('One last thing: ')
delay('s')
write('Go ahead and leave me. ')
delay('b')
write('I think I prefer to stay inside. ')
delay('m')
write('Maybe you\'ll find someone else ')
delay('sss')
write('to help you. ')
delay('b')
write('Maybe Black Mesa... ')
delay('s')
write('THAT WAS A JOKE. ')
sleep(1.5)
write('FAT CHANCE. ')
delay('b')
write('Anyway, this cake is great. ')
delay('ss')
write('It\'s so delicious and moist. ')
delay('ss')
write('Look at me still talking ')
delay('sss')
write('when there\'s science to do. ')
delay('s')
write('When I look out there, ')
delay('sss')
write('it makes me GLaD I\'m not you. ')
delay('s')
write('I\'ve experiments to run. ')
delay('sss')
write('There is research to be done. ')
delay('sss')
write('On the people who are ')
delay('s')
write('still alive. ')
sleep(0.5)
for i = 1, 255 do
    print()
end
write('PS: And believe me I am ')
delay('ss')
write('still alive. ')
delay('s')
write('PPS: I\'m doing science and I\'m ')
delay('ss')
write('still alive. ')
delay('s')
write('PPPS: I feel FANTASTIC and I\'m ')
delay('ss')
write('still alive. ')
print()
print()
write('FINAL THOUGHT: ')
print()
write('While you\'re dying I\'ll be ')
delay('ss')
write('still alive. ')
print()
print()
sleep(1)
write('FINAL THOUGHT PS: ')
print()
write('And when you\'re dead I will be ')
delay('ss')
write('still alive. ')
print()
print()
write('STILL ALIVE.')
sleep(3)
for i = 1, 255 do
    print()
end
write('Still alive.')
sleep(4)


```

In case that doesn't work I will be posting to pastebin:[ http://pastebin.com/t0yRAp3h]("http://pastebin.com/t0yRAp3h")[URL="http://pastebin.com/NZKCDuaB"]
[/URL]

---

