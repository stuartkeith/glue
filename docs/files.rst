Configuration files
==========================

Introduction
------------
``glue`` has around fifteen command line arguments, so adding all of them every time
you need to rebuild your sprites could be really annoying.

You can add to your sprites container or to your sprite folder a configuration file named ``sprite.conf`` and add inside
all the configuration you need::

    images
        ├── actions
        │   ├── add.png
        │   └── remove.png
        └── icons
        │   ├── comment.png
        │   ├── new.png
        │   └── rss.png
        └── sprite.conf

If for example you want to change the namespace and the default padding to all your sprites you can add this to your ``sprite.conf``::

    [sprite]
    namespace=my-sprites
    padding=20


If the ``actions`` images needs to be cropped and have a different padding, you can create a new ``sprite.conf`` file inside your ``actions`` folder::

    images
        ├── actions
        │   ├── add.png
        │   ├── remove.png
        │   └── sprite.conf
        └── icons
        │   ├── comment.png
        │   ├── new.png
        │   └── rss.png
        └── sprite.conf

All the configuration you add there will override the first configuration file::

    [sprite]
    crop=true
    padding=10

.. note::
    All the configuration you specify using the command line will override the configuration that comes from any configuration file.

Available configuration
-----------------------

This is all the available configuration you can add to your ``sprite.conf`` files.

======================== ======================================================================================
name                     default value
======================== ======================================================================================
padding                  '0'
margin                   '0'
algorithm                'maxside'
namespace                'sprite'
crop                     False
url                      ''
extension                'css'
optipng                  False
html                     False
ignore_filename_paddings False
size                     True
png8                     False
optipngpath              'optipng'
optipng                  False
separator                '-'
project                  False
quiet                    False
cachebuster              False
cachebuster-filename     False
global_template          '{{ all_classes }} { background-image: url({{ sprite_url }}); background-repeat: no-repeat; }\\n'
each_template            '.{{ class_name }} { background-position: {{ x }}px {{ y }}px; width: {{ width }}px; height: {{ height }}px; }\\n'
ratio_template           '\@media only screen and (-webkit-min-device-pixel-ratio: {{ ratio }}), only screen and (min--moz-device-pixel-ratio: {{ ratio }}), only screen and (-o-min-device-pixel-ratio: {{ ratio_fraction }}), only screen and (min-device-pixel-ratio: {{ ratio }}) { {{ all_classes }} { background-image: url({{ sprite_url }}); -webkit-background-size: {{ width }}px {{ height }}px; -moz-background-size: {{ width }}px {{ height }}px; background-size: {{ width }}px {{ height }}px; } }\\n'
======================== ======================================================================================

