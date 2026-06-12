---
title: "Anybody know Fourier Analysis?"
date: 2010-03-17
forum: The Cafe
---

### Post by Pogeymanz on 2010-03-17
Let's say a have a simple signal like [0,0,0,0,0,0,...,1,1,1,1,1,...,0,0,0,0,0,...,3,3,3,3]
and I want to interpolate it to have more points. I can use the Fast Fourier Transform and interpolate it just fine. Then I have Gibbs ringing in the plot.

Apparently I can use a "window function" to reduce the ringing somehow. Specifically I should be able to use a Hann window: [http://en.wikipedia.org/wiki/Window_function#Hann_window](http://en.wikipedia.org/wiki/Window_function#Hann_window)

My question is so basic that I may be laughed at, but what do I **do** with the window function? And why in the world should I think that it will help with the ringing?

---

### Post by Zoot7 on 2010-03-17
Window functions are normally used for reducing the effects of phenomena like spectral leakage or spectral broadening etc. To use a Window function just multiply the input signal by it before you parse it through an FFT (or whatever).

"Ringing" would normally arise from not having an adequate sample rate for the input signal. The sampling frequency has to be greater than at least twice the Nyquist frequency as to capture all the range of frequencies, otherwise you'll get higher frequencies "aliasing" down causing things like "Ringing".
[http://en.wikipedia.org/wiki/Nyquist_rate](http://en.wikipedia.org/wiki/Nyquist_rate)

---

### Post by Pogeymanz on 2010-03-17
> **Zoot7 said:**
> Window functions are normally used for reducing the effects of phenomena like spectral leakage or spectral broadening etc. To use a Window function just multiply the input signal by it before you parse it through an FFT (or whatever).

"Ringing" would normally arise from not having an adequate sample rate for the input signal. The sampling frequency has to be greater than at least twice the Nyquist frequency as to capture all the range of frequencies, otherwise you'll get higher frequencies "aliasing" down causing things like "Ringing".
[http://en.wikipedia.org/wiki/Nyquist_rate](http://en.wikipedia.org/wiki/Nyquist_rate)

Oh, I see. So I need to multiply the original signal by the window function and THEN interpolate it with FFT, etc? I was thinking the window function would be somehow applied to the already-interpolated signal.

---

### Post by Zoot7 on 2010-03-17
Oh, my bad I see you want to *interpolate* the input signal. The window function isn't really going to help in this case, it wouldn't be any harm to put it in none the less, but it's not going to help with the ringing you're seeing.

What you do when you interpolate is raise the sample rate by the interpolation rate, thus you introduce higher frequencey components into the signal, which of course you don't want.

To interpolate a signal do the follwing:
*Say your initial input signal has N samples.
*Define an array of I*N zeros size where I is your interpolation rate.
*Set every Ith sample of the new array to the original signals corresponding sample.
*Now the key part, you have to filter out the newly introduced higher frequencies. The best is to use a Low pass FIR filter of normalized cut off frequency 1/I.

That's interpolation in time, it can be done in the frequency domain too, but it's easier to understand when done in the time domain. 
It's a tad bit more technical as you can see. :)

Are you using MATLAB? If so I could put together some basic code to illustrate the principals to you.

---

