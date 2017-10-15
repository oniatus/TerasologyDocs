.. _concept_modules:

Modules
=======

Modules are extensions/modifications to the engine. A Terasology module is a java project on it's own, which is resolved similar to a library an lives in it's own sandboxed environment.
The module system is implemented the `gestalt module <https://github.com/MovingBlocks/gestalt>`_ library.

Structure of Modules
--------------------

- :code:`/src` - actual source code for custom functionality goes here. Usually this will be custom components and systems which extend the :ref:`entity_System`.
- :code:`/assets` - Resources related to the module can be placed here and will be located by the :ref:`asset_system`. Sub-categories for assets like prefabs or block definitions are structured in sub-directories.
- :code:`/deltas` and :code:`/overrides` - Modification directories for existing assets. These mechanics are described at `TutorialAssetSystem/Deltas-and-Overrides <https://github.com/Terasology/TutorialAssetSystem/wiki/Deltas-and-Overrides>`_.
- :code:`build.gradle` - internal build file, should not be edited.
- :code:`module.txt` - Configuration file for the module, similar to a maven :code:`pom.xml` or gradle build file. Have a look at the :ref:`module_txt` section for details.


.. _module_categories:

Categories
----------

Modules can be in different categories, indicated by flags in the :ref:`module_txt`.

+--------------+-------------------------------------------------------------------------------------------------------------------------------+
| Category     | Description                                                                                                                   |
+==============+===============================================================================================================================+
| Gameplay     | Game type / mode that may depend on a large number of modules and forces a particular style of play.                          |
+--------------+-------------------------------------------------------------------------------------------------------------------------------+
| Library      | No standalone purpose, purely utility for other modules.                                                                      |
+--------------+-------------------------------------------------------------------------------------------------------------------------------+
| World        | Adds world generator features.                                                                                                |
+--------------+-------------------------------------------------------------------------------------------------------------------------------+
| Asset        | Plain art / passive convent modules, possibly with prefabs or other definitions.                                              |
+--------------+-------------------------------------------------------------------------------------------------------------------------------+
| Augmentation | Plug and Play content that can be enabled and could work with gameplay modules but does not force particular gameplay itself. |
+--------------+-------------------------------------------------------------------------------------------------------------------------------+
| Special      | Special cases which do not belong to other categories.                                                                        |
+--------------+-------------------------------------------------------------------------------------------------------------------------------+



Namespace
---------

The common namespace for a module is :code:`org.terasology.<nameOfTheModule>.*`. It is recommended to name source packages accordingly, otherwise modules may not be built or loaded as expected. [#]_

.. [#] See `#2445 <https://github.com/MovingBlocks/Terasology/issues/2445>`_ for more details.

Guides
------

The :ref:`Modules Guide <developing_modules>` delivers further information about fetching and creating modules, dependencies and the sandbox environment.
