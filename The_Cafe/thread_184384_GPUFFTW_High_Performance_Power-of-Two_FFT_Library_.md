---
title: "GPUFFTW: High Performance Power-of-Two FFT Library using Graphics Processors"
date: 2006-05-29
forum: The Cafe
---

### Post by RAV TUX on 2006-05-29
What are you thoughts:


[http://gamma.cs.unc.edu/GPUFFTW/]("http://gamma.cs.unc.edu/GPUFFTW/")

**GPUFFTW versus cfft1d()on the CPU **

  We have observed considerable speedups with GPUFFTW over Intel Math Kernel library running on high-end multi-core CPUs. The following graph shows the * compute * timings for two test systems with high-end $1500-$2000 CPUs. Note that in both cases, GPUFFTW performs considerably faster. The cfft1d routine in the Intel Math Kernel library uses four threads to exploit the four available processors on the dual Opteron 280 processors and the dual 3.6 GHz HT Xeon processors. In practice, using the FFTW metric, our algorithm is able to achieve 6 GFLOPS of computational performance on a NVIDIA 7900 GPU. 


[[IMG]http://img218.imageshack.us/img218/8646/ffttimings0si.th.jpg[/IMG]]("http://img218.imageshack.us/my.php?image=ffttimings0si.jpg")

**Comparison of GPUFFTW with     previous approaches for performing 1D FFTs on the GPU **

  We have also compared the performance of GPUFFTW and libgpufft on a NVIDIA 7800 GTX GPU. Our algorithm uses stockham autosort whereas libgpufft is implemented using the BrookGPU compiler and uses an improved version of Cooley-Tukey FFT algorithm. Our results indicate a 3x performance improvement over libgpufft.

 **Introduction**

 GPUFFTW is a fast FFT library designed to exploit the computational performance and memory bandwidth on GPUs. Our library exploits the data parallelism available on current GPUs and pipelines the computation to the different stages of the graphics processor. Moreover, our library uses an efficient tiling strategy to further improve the memory performance of our algorithm. GPUFFTW can efficiently handle large real and complex 1-D arrays at 32-bit floating point precision on commodity GPUs. Furthermore, our FFT algorithm achieves comparable precision to the IEEE 32-bit FFT algorithms on CPUs even on large 1-D arrays. The library supports both Windows and Linux platforms.  Please refer to the documentation for details regarding the API and the contents of the distribution. Also, please read through the system requirements below before using the library.
 
  **System Requirements**
[LIST]
[*] **OS**:   Microsoft Windows XP/2000 and Linux
[*]**RAM**: Atleast a size of graphics processor video memory is required.
[*]**GPU**: NVIDIA GeForce/Quadro family card with support for the following OpenGL extensions:[LIST=1]
[*]EXT_framebuffer_object
[*]ARB_texture_rectangle
[*]ARB_fragment_program[/LIST] 
[*]The above requirements are met by NV30-based GPUs and above (GeForce FX and GeForce 6 series)
[*]The library has been tested on the following cards:[LIST]
[*]GeForce 7800/7900 GTX/GT/Go
[*]GeForce 6800 Ultra/GTO
[*]GeForce 5950 Ultra
[*]GeForce 5800
[*]Quadro FX 4000
[*] Laptop graphics cards: QuadroFX 700 Go, QuadroFX 1000 Go, QuadroFX 1400 Go, GeForce 7800/6800 Go
      For obtaining reasonably high performance, we recommend a PC with AGP8X/PCI-Express NVIDIA GeForce 6800 GT or faster GPU.[/LIST] 
[*]**Video RAM: **The Video RAM will determine the maximum array length that can be sorted on the GPU. A rough guideline for performing FFT on 32-bit floats is: Maximum array length in millions = Video RAM in MB / 32. Therefore, on a card with 256 MB VRAM, the maximum-length array which can be sorted is 256/32 = 8 Million real values or 4M complex values
[*]**Drivers: **Latest drivers from   NVIDIA (version 7772 or higher for windows, and 7664 for linux).[/LIST]**Note:**
[LIST]
[*]**ATI cards: **ATI cards are not supported in the present release of GPUFFTW mainly due to the lack of suport for ARB_texture_rectangle in fragment programs on current ATI drivers. These cards will be supported in future releases.
[*] ** Higher Dimensional FFTs ** Our current code only handles 1D power-of-two single-precision FFTs. Future releases may include 2D and 3D FFTs.[/LIST] 
      ** Related Links **

     
    [UNC GAMMA Group]("http://www.cs.unc.edu/%7Egeom/")
    [ GPGP: General     Purpose Computation using Graphics Hardware ]("http://www.cs.unc.edu/%7Egeom/hardware/index.shtml")

 ** Publications **
[LIST]
[*] *Efficient Memory Model for Scientific Algorithms on Graphics Processors*, 
  Naga K. Govindaraju, Scott Larsen, Jim Gray,  Dinesh Manocha 
  UNC Tech. Report 2006.[/LIST]       ** Acknowledgements **

 We would like to thank Jim Gray for useful discussions and encouragement. Many thanks to Scott Larsen, John Owens, Daniel Horn, David Tuft and members of UNC GAMMA group for helping us compare against optimized libraries on GPUs and CPUs. 
     
 ** Research Sponsors **
[LIST]
[*] Army Modeling and Simulation Office
[*] Army Research Office
[*] Defense Advanced Research Projects Agency
[*] RDECOM
[*] NVIDIA Corporation[/LIST]   

**GPUFFTW: Download Version 1.0**



  We ask that you fill out a [request form]("http://gamma.cs.unc.edu/GPUFFTW/request.html") to identify yourself and indicate your interest in GPUFFTW.  The request form will automatically direct you to our source package once you fill in the details and submit the request.
 This release contains documentation, the source code for the GPUFFTW library, and an example program. GPUFFTW can be compiled on the Win32/Linux platforms and requires a programmable NVIDIA graphics card. Visual Studio .NET solution files for use on windows platform are included. 
 GPUFFTW is ***free for noncommercial use only***. Click [here]("http://gamma.cs.unc.edu/GPUFFTW/terms.html") for the terms of this distribution. 
 Click on a version link and fill the [request form]("http://gamma.cs.unc.edu/GPUFFTW/request.html") to  download the distribution. 


 **Version History**

 Version 1.0: [GPUFFTW1.0]("http://gamma.cs.unc.edu/GPUFFTW/request.html")

 Requires a programmable NVIDIA Graphics Card (NVIDIA GeForceFX series, GeForce 6 series, and GeForce 7 series), latest NVIDIA drivers (7772 or higher), and [GLUT libraries ]("http://www.opengl.org/resources/libraries/glut/glut_downloads.html").   

Note: We will support ATI GPUs in future releases. NVIDIA linux drivers may have some performance overhead. Performance will also vary with the GPU used, and for reasonable performance, we recommend a PC with AGP8X or PCI-Express NVIDIA GeForce 7800 GT or faster cards. 





Author: [Naga K. Govindaraju]("http://www.cs.unc.edu/%7Enaga") 
 Maintained by: [EMAIL="naga@cs.unc.edu"]naga@cs.unc.edu[/EMAIL] 
 Copyright 2006 
 Last Modification: May 22, 2006

---

### Post by almahtar on 2006-05-30
I saw an article about this on either LinuxNews or Slashdot.  I had a few questions....
#1.  What on earth is FFT?
#2.  How will this impact the market? Like... it's hard to tell clearly what this particular technological advance actually *does* from the article.

---

### Post by hesee on 2006-05-30
[QUOTE=almahtar]I saw an article about this on either LinuxNews or Slashdot.  I had a few questions....
#1.  What on earth is FFT?
#2.  How will this impact the market? Like... it's hard to tell clearly what this particular technological advance actually *does* from the article.[/QUOTE]

FFT is Fast Fourier Transform. It (and its variations) is a very important and widely used computational algorithm to calculate DFT. Basically DFT transforms signal from frequency plane to time plane, but there is much more applications.

So these guys made a library, which can compute FFT's much faster in graphics card's GPU than in main CPU, right?

---

