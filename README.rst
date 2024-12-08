Support for using Giac within SageMath

Introduction
============

Giac is a full-featured, open source mathematics library written by
Bernard Parisse:

  https://www-fourier.ujf-grenoble.fr/~parisse/giac.html

For many years, SageMath has included an interface to Giac based on
the GiacPy python interface by Frederic Han:

  https://pypi.org/project/giacpy/

Now this interface has been split off into a separate package. The
main reason you would want to install it is to add Giac as a backend
for SageMath's ``integrate`` command. For example, without this
package, Sage cannot integrate the following example::

    >>> from sage.all import *
    >>> from sage.libs.giac import libgiac
    >>> x = SR.symbol("x", domain="real")
    >>> libgiac.integrate(2*min_symbolic(x,2*x),x).sage()
    -1/2*x^2*sgn(x) + 3/2*x^2

After installing sagemath-giac, Sage will automatically gain the
ability to do these integrals. Of course, you also gain access to the
rest of the Giac library, with easy conversions to and from Sage
objects.

Testing
=======

A few doctests within the module (and this README) ensure that
everything is working. You can run them from the repository or from a
release tarball using::

    PYTHONPATH=src python -m sage.doctest \
      README.rst \
      src/sage/libs/giac/*.py \
      src/sage/libs/giac/*.pyx

Or, if you have pytest installed, with simply::

    pytest
