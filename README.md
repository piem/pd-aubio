pd-aubio
========

pd-aubio contains various externals for PureData using the aubio library.

For more information, see:

  * [aubio homepage](http://aubio.org)
  * [puredata homepage](http://puredata.info)

Building
--------

pd-aubio uses waf. To configure and build it, run:

        $ ./waf configure build

If you have built and installed aubio with an unusual `--prefix` location, you
will need to set `PKG_CONFIG_PATH` accordingly.

For instance, to build against aubio installed in `/var/tmp/opt-aubio`:

        $ PKG_CONFIG_PATH=/var/tmp/opt-aubio/lib/pkgconfig \
            ./waf distclean configure build install \
            --prefix=/var/tmp/opt-aubio

If you have installed aubio with the `--destdir` option, you will also need to
set `CFLAGS` and `LDFLAGS`.

For instance, you could use the following to use aubio installed in
`/var/tmp/dist-aubio`:

        $ PKG_CONFIG_PATH=/var/tmp/dist-aubio/usr/local/lib/pkgconfig \
            CFLAGS=-I/var/tmp/dist-aubio/usr/local/include \
            LDFLAGS=-L/var/tmp/dist-aubio/usr/local/lib \
            ./waf distclean configure build install \
            --destdir=/var/tmp/dist-aubio

Installing
----------

To install the aubio external for puredata on your system, run the following as
root:

        # ./waf install

Running
-------

To load the external, start pd as follows

        $ pd -lib aubio

If the external file (`aubio.pd_linux`, `aubio.pd_darwin`, or `aubio.dll`) is
installed in a strange location, add the path to this file to with `-path`.

        $ pd -path /var/tmp/dist-aubio/usr/lib/pd/extra/aubio -lib aubio

Alternatively, you can create an object `[aubio]` to initialize the external.
If the external is found in your path, it will be automatically loaded.

If you want to use the external without installing it, you will need to set
your `LD_LIBRARY_PATH` to include the path to the aubio library.
