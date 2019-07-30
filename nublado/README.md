# Python in Astronomy 2019
# LSST Stack Tutorial 

LSST data will be available through the **LSST Science Platform** which consists of a few aspects including the

- Portal Aspect
- API Aspect: e.g. data access via IVOA TAP (1.1) Service, supports IVOA ADQL 2.1 queries, query pixels via IVOA SODA service. CAOM2 data model
- **Notebook Aspect**

This demo is a sneak preview of how you’ll interact with the LSST data via the notebook aspect. The only prerequisite is a computer with an internet connection in a modern browser. 

Authentication is through your github account. Please send your github id to Chris Waters or Nate Lust on Slack for access. 

Once they give you the greenlight, 

1) go to: http://nublado.lsst.codes

 - Select "Science Platform Notebook Aspect"
 - Spawn an container. Choose `w_2019_29` and a small size.

These notebooks are designed to analyze an image that you will process first with the
LSST stack.  The raw data is available on the LSST Science Platform at
`/project/shared/data/ci_hsc_small`. Users should copy this to their home
directory to work on.

2) Select "New Terminal" at the bottom. (If you can't find this, go to _File_ > _New Launcher_)

`cp -r /project/shared/data/ci_hsc_small ~/ci_hsc_small`

After copying, users will need to run `processCcd.py` at a terminal to process
the raw data into a finished, calibrated exposure and associated source catalog.
You can access a terminal inside the JupyterLab environment.  

3) To setup the terminal environment for running LSST stack commands, run:

```
source /opt/lsst/software/stack/loadLSST.bash
setup lsst_distrib
```
This configures paths and environment variables to select the software you want
to use.

4)  To run the initial LSST processing stages, use the command: 
```
processCcd.py /home/YOUR_USERNAME/ci_hsc_small --rerun isr --id visit=903334 ccd=16 --config isr.doWrite=True
```
where `isr` is a RERUN_NAME is a name of your choosing; each time you process data, you
should give it a new rerun name.

Now you have an output calibrated image and source catalog to explore. Explore the available notebooks. 

## Notebooks
We recommend that you start with these notebooks:

- `notebooks/notebook-demo/AAS_2019_tutorial/intro-process-ccd`
 - Intro to LSST stack. Background info for the command you ran above. Also examples of source extraction, measurement, background estimation, and PSF estimation.
-  `notebooks/notebook-demo/AAS_2019_tutorial/Firefly` 
 - Intro to image viewer. Note you can get the url with the display object's `.getClient().get_firefly_url()` method.
- `notebooks/notebook-demo/Firefly` 
 - Intro to image viewer that does not require `processCcd.py` to be run ahead of time. It fetches products on shared disk.
-  `notebooks/notebook-demo/AAS_2019_tutorial/intro-deblending` 
 - Working with catalogs and examples of running detection, deblending, and source measurement.


## Resources

- https://pipelines.lsst.io/getting-started/
  - Tutorial and helpful reference on similar topics we’re covering today. 
- https://pipelines.lsst.io/v/daily/
  - In-progress documentation on all of the Tasks and functions in the Stack
- https://community.lsst.org/
  - Q&A about LSST; someone might have already answered your question here.
- https://github.com/LSSTScienceCollaborations/StackClub/
  - “Stack Club” is a group of science users exploring the LSST Stack. Many helpful
notebooks, all on github.


