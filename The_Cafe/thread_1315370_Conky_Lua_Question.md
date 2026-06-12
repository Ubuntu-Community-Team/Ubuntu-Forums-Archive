---
title: "Conky Lua Question"
date: 2009-11-05
forum: The Cafe
---

### Post by pbeesley on 2009-11-05
Can I have an if statement in a lua script to change the colour (I'm english and that's how you spell colour....stupid firefox spellcheck) of a ring based on the value of the arg?

something like this

        arg='cpu1',
        max=100,
        if value >80 then
        fg_colour=RED,
        else if value >60 then
        fg_colour=YELLOW,
        else if 
        fg_colour=GREEN

is that do-able?

Thanks Guys :rolleyes:

---

### Post by pbeesley on 2009-11-05
or something like this
```
{             
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0.1,
if arg < 60 then
                fg_colour=0xHEXFORGREEN
elseif arg < 80 then 
                fg_colour=0xHEXFORYELLOW
else 
        fg_colour=0xFF0000, (RED)
end
        fg_alpha=1,
        x=120, y=160,
        radius=102,
        thickness=7,
        angle=90
    },


```

---

