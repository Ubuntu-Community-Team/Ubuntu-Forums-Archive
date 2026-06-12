---
title: "Using Scilab, Have a look please!!!"
date: 2006-05-10
forum: The Cafe
---

### Post by leeyee on 2006-05-10
Hi guys,
Do you use Scilab? I'm a student from an Engineering College, and study Information Engineering. It's neccessary for me to use these computing software to do some signal process or just plot some simple curve. I  post here just want to meet some friends who are also learning these courses or just using Scilab as one of your tools.:p That's odd I can't find a forum of SCILAB although i did a GOOGLE for it, Ugh!
Thank you guys!:-?  And sorry for my poor English:KS

---

### Post by hesee on 2006-05-10
I've been using Matlab in my studies(telecomms/cellular/dsp). I tried to start using Scilab, but the commands were different/missing so I decided to stay Matlab/windows till i graduate. But Scilab looks very similar, and can probably do most of the same things. Surprising, that there is not Scilab forum (or can anyone correct this?).

---

### Post by Kannisto on 2006-05-10
[QUOTE=hesee]I've been using Matlab in my studies(telecomms/cellular/dsp). I tried to start using Scilab, but the commands were different/missing so I decided to stay Matlab/windows till i graduate. But Scilab looks very similar, and can probably do most of the same things. Surprising, that there is not Scilab forum (or can anyone correct this?).[/QUOTE]
Octave is great too try it out. Scilab just seems a bit unfinished (tamili fonts etc.)
Have you asked how much would it cost to change your win license to Unix license?

---

### Post by hesee on 2006-05-10
[QUOTE=Kannisto]Octave is great too try it out. Scilab just seems a bit unfinished (tamili fonts etc.)
Have you asked how much would it cost to change your win license to Unix license?[/QUOTE]
Actually, I was using Matlab in school lab. That's why i wanted an alternative, to be able to do some studies at home. Thanks for the Octave tip, have to try that one out.

---

### Post by hizaguchi on 2006-05-10
Never used Scilab, but I'll 2nd the Octave reccomendation.  It may be missing some kind of advanced feature that I have no use for, but for my undergrad mechanical engineering it's more than enough.  I like it better than Matlab really.  Especially combined with Kate, since the syntax highlighting is better than Matlab's editor and there's a built-in terminal to run your code right there in the same window.

---

### Post by leeyee on 2006-05-10
Aha....Thanks for you guys recommended Octave! However, I had used Octave for several times before, it seems that it has no graphic commands, or it has no GUI?

---

### Post by leeyee on 2006-05-11
Hi guys,
I encountered a compute problem with scilab, which is to plot the curve of the following function y:

```
Y=(2/(pi^2*BT))*(Si(pi*BT))^2
```
where BT is a variable matrix defined in a interval (0,1) and Si(u) is the sine integral function which is defined as the integral of the sin(x)/x from 0 to u. 
This is a problem I need to do comes from the <<Communication System>>, anyone can help me with a scilab programming to plot the curve? I had did the forllowing program, but it seems not work.:-?  It plotted an apparent wrong curve.
```

clear
xbasc()
BT=0.000001:0.01:1;


//To define the si function
ss=zeros(BT);
deff('[y]=f(x)','y=sin(x)/x');
function SI=si(u)
for i=1:1:length(BT)
   uu=u(i);
   ss(i)=intg(0,uu,f);
end
SI=ss;
endfunction

y=(2/(%pi^2*BT)).*((si(%pi*BT))^2);
plot2d(BT,y)
xtitle("Get maximum value","BT","y")
xgrid()

```
Thank you very much!

---

### Post by hizaguchi on 2006-05-11
[QUOTE=leeyee]Aha....Thanks for you guys recommended Octave! However, I had used Octave for several times before, it seems that it has no graphic commands, or it has no GUI?[/QUOTE]
Do you mean for plotting functions?  If so, you just need to get gnuplot.

Or if you're talking about a user interface, there is Koctave (need Dapper for that), but I like Kate better myself because it keeps everything in one window.

---

### Post by leeyee on 2006-05-12
Okay, I think I should be stick to SCILAB. Now what I'm wondering is somebody plot the function I yesterday post for me. Thanks you guys!
Here is the right curve which  i saw from the "Standard Answers"

---

### Post by leeyee on 2006-05-15
Nobody could help me? 55555..................

---

### Post by u04f061 on 2006-05-31
[QUOTE=leeyee]Hi guys,
I encountered a compute problem with scilab, which is to plot the curve of the following function y:

```
Y=(2/(pi^2*BT))*(Si(pi*BT))^2
```
where BT is a variable matrix defined in a interval (0,1) and Si(u) is the sine integral function which is defined as the integral of the sin(x)/x from 0 to u. 
This is a problem I need to do comes from the <<Communication System>>, anyone can help me with a scilab programming to plot the curve? I had did the forllowing program, but it seems not work.:-?  It plotted an apparent wrong curve.




which font u use in scilab?
can u tell me how to set english font which is readable?i can't read even my own written code in scilab.that is why i am not using it and trying to find the ways to install matlb.
 plz reply me positively
thnx

---

