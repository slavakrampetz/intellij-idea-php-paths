## Problem

In all our projects we are separating code / public part. Standard path suggestion helper doesn't work out of box in IntelliJ IDE's (IDEA, PHPStorm, WebStorm).

[slide1](img/problem-01.png)

[slide2](img/problem-02.png)

So each time on new project I have to find how to make work this very useful feature.

## Solution

**Example project**

1. Most PHP code located in folder ``/back/``, including PHP templates
2. Node modules located in folder ``/node_modules/`` (surprisingly!)
3. Static files located in ``/www/static/`` folder
4. Content files located in ``/www/content/`` folder
5. Some generated JS files - in ``/www/static/prj/js/compiled/`` folder
6. Temporary files, logs etc placed to ``/var/`` folder
7. We are use Bulma Sass files from node modules

**Step 1. Mark directories.**

It can be done directly in 'Project' sidebar or (preferred) in 'Project structure' dialog.

Mark folders:
- ``/var/``, ``/node_modules/`` as 'Excluded'
- ``/www/``, ``/back/``, ``/node_modules/bumla/sass/`` as 'Source'
- ``/www/content/``, ``/www/static/prj/js/compiled/`` as 'Excluded'

Example: [Project Structure](img/ide.modules.png)

**Step 2. Configure Deployment server**

1. Where: Menu / Tools / Deployment / Configuration
2. Click '+', enter name and choose 'In place'
3. Tab 'Connection', choose 'Web server root URL'.
  [Example](img/ide.deployment-connection.png)
4. Tab 'Mappings', setup mappings:
  - ``/www/`` -> ``/``
  - ``/back/core/code/`` -> ``/script/core/``
  - ``/back/prj/code/`` -> ``/script/prj/``
  [Example](ide.deployment-mappings.png)

That's all. Sometimes you'll need to restart IDE for it work, but in most cases it's enough.



