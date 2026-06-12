---
title: "server 14.4. Theano cannot find libopenblas, has numpy- and scipy-problems"
date: 2014-09-07
forum: Server Platforms
---

### Post by Zatarion on 2014-09-07
Hey folks,

I am not very experienced with Linux and have a group of servers with Ubuntu 14.04 LTS and try to use Theano. Sadly on testing the installation says it cannot find libopenblas and have trouble with numpy. Now scipy also crashes.
I followed this guide: [http://deeplearning.net/software/theano/install_ubuntu.html](http://deeplearning.net/software/theano/install_ubuntu.html) and try to run the code/rba.py from the deeplearing theano demo package ([http://deeplearning.net/tutorial/gettingstarted.html#index-0](http://deeplearning.net/tutorial/gettingstarted.html#index-0)).

I installed libopen-blas, python-numpy, python-scipy, python-nose with apt-get before and Theano with pip. (FYI there is also mpi4py and an additional anaconda installation in /opt.)


> rumler@sabik:~/DeepLEarningTutorials/code$ python rbm.py
... loading data
[...]
Problem occurred during compilation with the command line below:
g++ -shared -g -O3 -fno-math-errno -Wno-unused-label -Wno-unused-variable -Wno-write-strings -Wl,-rpath,/usr/lib -D NPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION -m64 -fPIC -I/usr/lib/python2.7/dist-packages/numpy/core/include -I/usr/include/python2.7 -o /mnt/antares_raid/home/rumler/.theano/compiledir_Linux-3.13.0-29-generic-x86_64-with-Ubuntu-14.04-trusty-x86_64-2.7.6-64/tmpwjevx9/240c5e3dff498a7e26b3d4b0a8e7d01e.so /mnt/antares_raid/home/rumler/.theano/compiledir_Linux-3.13.0-29-generic-x86_64-with-Ubuntu-14.04-trusty-x86_64-2.7.6-64/tmpwjevx9/mod.cpp -L/usr/lib -lpython2.7 -lblas
/usr/bin/ld: cannot find -lblas
collect2: error: ld returned 1 exit status
[...]
Exception: ('The following error happened while compiling the node', Dot22(Subtensor{int64:int64:}.0, W01), '\n', 'Compilation failed (return status=1): /usr/bin/ld: cannot find -lblas. collect2: error: ld returned 1 exit status. ', '[Dot22(<TensorType(float64, matrix)>, W01)]')
rumler@sabik:~/DeepLEarningTutorials/code$ THEANO_FLAGS=blas.ldflags="-L/usr/lib -libblas" python rbm.py
... loading data
WARNING (theano.tensor.blas): We did not found a dynamic library into the library_dir of the library we use for blas. If you use ATLAS, make sure to compile it with dynamics library.

The config is set to -lblas too.
> rumler@sabik:~/DeepLEarningTutorials/code$ python -c 'import theano;  
print theano.config' | grep blas
blas.ldflags (<type 'str'>)
     Doc:  lib[s] to include for [Fortran] level-3 blas implementation
     Value:  -L/usr/lib -lblas

The libs:
> rumler@sabik:/usr/lib$ ls | grep blas
libblas
libblas.a
libblas.so
libblas.so.3
libblas.so.3gf
libgslcblas.so.0
libgslcblas.so.0.0.0
libopenblas.a
libopenblas-base
libopenblas.so
libopenblas.so.0
openblas-base

I tried different names for the lib by running the script with: THEANO_FLAGS=blas.ldflags="-L/usr/lib -libopenblas" python [rbm.py]("http://rbm.py/")
The error was still the same but with the given lib-name. I also tried setting LD_LIBRARY_PATH to /usr/lib, no change. 

> rumler@sabik:/usr/lib$ sudo ldconfig -v | grep blas 
        libgslcblas.so.0 -> libgslcblas.so.0.0.0
         libblas.so.3 -> libblas.so.3gf
         libopenblas.so.0 -> libopenblas.so.0


Found a post that told me to create a softlink from libopenblas-base to openblas-base and  
libopenblas.so to libopenblas.so.0 for the linker but that didn't help too.


After removing and reinstalling libopenblas again and numpy and scipy afterwards too I get this error (got it in some states before too):
> rumler@sabik:~/DeepLEarningTutorials/code$ python rbm.py
... loading data
/usr/local/lib/python2.7/dist-packages/theano/scan_module/scan_perform_ext.py:85: RuntimeWarning: numpy.ndarray size changed, may indicate binary incompatibility
  from scan_perform.scan_perform import *
It locks there until I ctrl+c it.

Pip also had a numpy, I deinstalled it there and removed and reinstalled it with apt-get again, and then libopenblas one more time. Maybe that was not a good idea?

I checked numpy and scipy with their test suite, numpy looks fine, scipy not. Not sure if there is a dependency.
> rumler@sabik:/usr/lib$ python
Python 2.7.6 (default, Mar 22 2014, 22:59:56)
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import numpy
>>> numpy.test('full')
[...]
Ran 4957 tests in 214.183s
OK (KNOWNFAIL=5, SKIP=6)
<nose.result.TextTestResult run=4957 errors=0 failures=0>

>>> import scipy
>>> scipy.test('full')
[...]
/usr/lib/python2.7/dist-packages/numpy/core/include/numpy/npy_1_7_deprecated_api.h:15:2: warning: #warning "Using deprecated NumPy API, disable it by " "#defining NPY_NO_DEPRECATED_API NPY_1_7_API_VERSION" [-Wcpp]
 #warning "Using deprecated NumPy API, disable it by " \
  ^
................................................................................................
======================================================================
ERROR: test_fitpack.TestSplder.test_kink
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/nose/case.py", line 197, in runTest
    self.test(*self.arg)
  File "/usr/lib/python2.7/dist-packages/scipy/interpolate/tests/test_fitpack.py", line 329, in test_kink
    splder(spl2, 2)  # Should work
  File "/usr/lib/python2.7/dist-packages/scipy/interpolate/fitpack.py", line 1186, in splder
    "and is not differentiable %d times") % n)
ValueError: The spline has internal repeated knots and is not differentiable 2 times


----------------------------------------------------------------------
Ran 10001 tests in 869.534s


FAILED (KNOWNFAIL=158, SKIP=207, errors=1)
<nose.result.TextTestResult run=10001 errors=1 failures=0>





I have no idea what I can do - linker problem? Trouble with blas lib[s]? Incompatible package versions?

Thanks for any help!

---

