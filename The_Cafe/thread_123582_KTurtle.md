---
title: "KTurtle"
date: 2006-01-30
forum: The Cafe
---

### Post by 1337sithlord on 2006-01-30
Anyone ever use KTrutle?  Ive used Logo before and thought a simpler version of it might come in handy for fast easy programming.  It was then that I realized it can only do +,-,*,/ not even ^.  It sucks at math.  

I thought I should solve my own problems, the spirit of open-source software afterall... customizing the program right?  I made my own algorithms for all sorts of math that it should be able to do, thinking I was being productive.

I thought what im about to post would go in the how-to forum since it extends the capabilities of the program but its really more of a rant.  The stupid compiler doesnt even work.  If anyone else has ever used it... do you get errors saying it doesnt recognize "]", "[" or "else" even though the words are essential to the syntax and their uses are explained in the help file?

Its a terrible program IMO that works half of the time at best and I already sent the Edutainers that made it an e-mail about it.  It might be because Im not using KDE but I doubt it.  If anyone has better luck with KTurtle than I do, or knows how to make it "not suck" in Python, heres some script that you can enter in to KTurtle to make it faintly approach a real programming language.

```

learn power x,a,b [
  # the all inclusive function accepting rational exponents
  if (remainder a,1 == 0) and (remainder b,1 == 0)[
    x = exponent x,a
    return radical x,b
  ]
  else
  [
    message "Exponents must be rational"
  ]
]

learn exponent x,n[
  # uses repeated multiplication to accomplish exponentiation
  y = 1
  if n > 0 [
    repeat n [
      y = y*x
    ]
    return y
  ]
  else
  [
    if x == 0 [
      message "Infinity: Cannot divide by 0"
    ]
    else
    [
      repeat n*-1[
        y = y*x
      ]
      return 1/y
    ]
  ]
]

learn radical x,n[
  # approximates the results of radicals to a reasonable accuracy
  if remainder n,2 == 0[
    upper = x
    lower = 0
    if x < 0[
      message "Complex: Multiply answer by i"
      x = x * -1
      ]
      else
      [
    if x >= 0[
      upper = x
      lower = 0
    ]
    else
    [
      upper = 0
      lower = x * -1
    ]
  ]
  while not((exponent y,n <= x + 0.001) and (exponent y,n >= x - 0.001))[
    y = (upper + lower)/2
    if exponent y,n > x[
      lower = y
      ]
      else
      [
      upper = y
    ]
  ]
  return y
]

learn remainder x,n[
  # increments a number to return the remainder of a division
  y = 1
  while (n * y) < x[
    y = y + 1
  ]
  return x - (n * y)
]

learn factorial x[
  # a factorial function
  y = 1
  a = 1
  if remainder x,1 == 0[
    if x > 0[
      repeat x[
        y = y * a
        a = a + 1
      ]
      return y
      ]
      else
      [
      x = x*-1
      repeat x[
        y = y * a
       a = a + 1
      ]
      return y*-1
    ]
    ]
    else
    [
    message "Factorial arguements must be integral"
  ]
]

learn invfactorial x[
  # an inverse factorial function
  a = 1
  if x > 0[
    y = x
    while y > 1[
      y = y/a
      a = a + 1
    ]
    if y < 1[
      message "Factorial arguements must be integral"
      ]
      else
      [
      return a
    ]
  ]
  else
  [
    y = x * -1
    while y > 1[
      y = y/a
      a = a + 1
    ]
    if y < 1[
      message "Factorial arguements must be integral"
    ]
    else
    [
      return a * -1
    ]
  ]
]

learn sine x[
  # approximates sine in radians to a reasonable accuracy
  n = 1
  y = 0
  repeat 100[
    y = y + ((exponent -1,(n-1))/factorial (2*n-1))*(exponent x, (2*n-1))
  ]
  return y
]

learn cosine x[
  # approximates cosine in radians to a reasonable accuracy
  n = 0
  repeat 100[
    y = y + (((exponent -1,n)*(exponent x,2*n))/factorial 2*n)
  ]
  return y
]

learn tangent x[
  # approximates tangent in terms of sine and cosine
  return (sine x/cosine x)
]

learn cotangent x[
  # approximates cotangent in terms of sine and cosine
  return (cosine x/sine x)
]

learn secant x[
  # approximates secant in terms of cosine
  return (1/cosine x)
]

learn cosecant x[
  # approximates cosecant in terms of sine
  return (1/sine x)
]

learn hypsine x[
  # approximates hyperbolic sine to a reasonable accuracy
  return (0.5 * ((exponent 2.71828,x)-(exponent 2.71828,(x*-1))))
]

learn hypcosine x[
  # approximates hyperbolic cosine to a reasonable accuracy
  return (0.5 * ((exponent 2.71828,x)+(exponent 2.71828,(x*-1))))
]

learn arcsine x[
  # approximates inverse sine to a reasonable accuracy
  n = 1
  y = 0
  repeat 100[
    y = y + (exponent 2*x,2*n)/((exponent n,2)*((factorial 2*n)/factorial n * factorial n))
  ]
  return radical (0.5*y),2
]

learn arctangent x[
  # approximates inverse tangent to a reasonable accuracy
  n = 0
  y = 0
  repeat 100[
    y = y + ((exponent -1,n)*(exponent x,2*n+1)/(2*n+1))
  ]
  return y
]

learn arccosine x[
  # approximates inverse cosine in terms of inverse tangent
  return arctangent (radical (1 - (exponent x,2))/x)
]

learn arccosecant x[
  # approximates inverse arccosecant in terms of arcsine
  return arcsine(1/x)
]

learn arcsecant x[
  # approximates inverse arcsecant in terms of arccosine
  return arccosine (1/x)
]

learn arccotangent x[
  # approximates inverse cotangent in terms of arctangent
  return arctangent (1/x)
]

learn logarithm x,b[
  # approximates the results of logarithms to a reasonable accuracy
  if x > 0[
    upper = 999999999
    lower = -999999999
    while not((exponent b,y <= x + 0.001) and (exponent b,y >= x - 0.001))[
      y = (upper + lower)/2
      if exponent b,y > x[
        lower = y
      ]
      else
      [
        upper = y
      ]
    ]
  ]
  else
  [
    message "Logarithm arguements must be positive"
  ]
]

```

---

