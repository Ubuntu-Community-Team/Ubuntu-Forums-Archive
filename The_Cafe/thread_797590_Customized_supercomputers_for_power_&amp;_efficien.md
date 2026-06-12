---
title: "Customized supercomputers for power &amp; efficiency..."
date: 2008-05-17
forum: The Cafe
---

### Post by Sporkman on 2008-05-17
[http://www.technologyreview.com/Infotech/20773/](http://www.technologyreview.com/Infotech/20773/)

> [B]A Smarter Supercomputer
[/B]
A new design could run ultrahigh-resolution climate models.
By Kate Greene

Despite all the horsepower of today's supercomputers, none are powerful enough to run algorithms that predict future weather down to the kilometer--a resolution that would allow researchers to model cloud behavior, improving overall accuracy of climate models and enabling better policy decisions on global warming. But now, researchers at Lawrence Berkeley National Laboratory, in Berkeley, CA, have designed a new type of supercomputer that could be powerful enough to run models with kilometer-scale precision. In addition, the proposed supercomputer, which leverages chip design technology from cell phones and MP3 players, would be hundreds of times more power efficient than any other supercomputer, making it more cost effective to run.

"Right now with supercomputers, money is the obstacle to building a bigger system to tackle bigger problems," says John Shalf, a computer scientist at Lawrence Berkeley National Laboratory. Using today's technology, a supercomputer capable of running high-resolution climate models would produce an energy bill of about $150 million a year, Shalf says. But by building a supercomputer with processors that are fine-tuned to save power, similar to the approach used in the mobile electronics industry, Shalf and his coworkers expect to be able to run a supercomputer for a fraction of the cost.

The Berkeley supercomputer is part of an effort by climate scientists to bring more computational power to highly complex climate models. Earlier this month, the National Center for Atmospheric Research, in Boulder, CO, announced that it will use an IBM supercomputer to look at the effects of climate change. The Berkeley supercomputer would, however, be a vast improvement because it could be far more energy efficient.

General-purpose processors, such as those in personal computers, have become powerful and cheap enough that many researchers simply wired up clusters of these standard processors to run intense computational tasks. While this approach works for a number of scientific problems, it fails for high-resolution climate models: the computation simply requires too much power.

Whereas a general-purpose processor is built to handle a range of operations, an iPod processor, for instance, is specialized for only a small number of tasks. The Berkeley researchers used software from Tensilica, a chip manufacturer in Santa Clara, CA, that develops chips for Motorola, to build a core with only the necessary functions. In addition, the researchers custom-designed the chip's memory and communication structure between cores to reduce inefficiencies, minimizing power consumption.

In total, the supercomputer will consist of 20 million processing cores. The researchers estimate that, with 32 cores on a chip about the size of a matchbook, the entire supercomputer will fill a space the size of half a tennis court. By the end of the year, the researchers expect to be able to simulate a climate model on tens of cores. This approach will allow the researchers to change the hardware to better fit the model, as well as modify the model to fit the hardware. "Instead of building a computer and then throwing a science problem to it, we're looking at the science problem and building a computer to fit the problem," says Shalf.

The specialized climate model, which is built by researchers at Colorado State University, splits the globe into 20 million cells--one for each processor--and will be able to track the movement of storm systems and weather fronts. "Clouds are the most poorly simulated parts of the climate system," says Michael Wehner, a climate researcher at the Berkeley lab. "And that has a lot of consequences."

Currently, climate models estimate the behavior of clouds at a resolution of hundreds of kilometers. This means that similar climate models produce drastically different results. What's more, higher-resolution models are important when making policy decisions at the regional level, Wehner says. For instance, governments can decide whether or not to move crops, budget for more water during potential future droughts, or improve infrastructure in coastal cities. "Improved models should make those decisions easier to justify," Wehner says.

Still, it's unclear whether the Berkeley researchers' supercomputer design will actually save money in the long run, as the design and manufacturing costs can run to millions of dollars. And as the researchers dive deeper into testing the design, there could be challenges with designing the inter-chip communication system. "The problem when you put many of [the cores] together is that there are often inefficiencies in aggregating them," says Mark Horowitz, a professor of electrical engineering and computer science at Stanford University, in Palo Alto, CA. "It's a really interesting idea," he says, "but it's not clear whether it is going to be successful or not."


---

### Post by aimran on 2008-05-17
I've been a fan of task specific microprocessor for years! Thanks for this info!

---

