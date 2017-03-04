# Open Data in Context

Translating government data for the rest of us.

[![NYC](attn_grab_pics/unsplash/nasa-43569.jpg)](https://unsplash.com/photos/_SFJhRPzJHs)

This repository contains materials for [BetaNYC's School of Data](https://schoolofdata.nyc/) workshop "Open Data in Context". Note that this repository is intended to be updated every once in a while!

###### Authors:
Eve Ahearn [@eveahe](https://twitter.com/eveahe) & Olga Ianiuk


## Exercises

**H-1B Visa Program Disclosure Data**

> ... Currently, foreign work visas are allocated by lottery and demand is at an all-time high, with over 236,000 petitions to the 2017 H-1B lottery. Driven by the United States Citizenship and Immigration Services (USCIS), the lotto takes place annually in April and sets aside 65,000 visas into a category deemed “general”, with 20,000 additional visas set aside for Masters students (at a U.S. institution). Depending on how quickly the quota for each category is reached, the USCIS will then do a random lottery for remaining visas ...
>
>-- <cite>[from the piece for the Fortune](http://fortune.com/2017/02/08/h-1b-visa-donald-trump-startups-entrepreneurs/) by Hicham Oudghiri, Enigma CEO</cite>

What can we learn about people who have had visas approved?

[![H1B](attn_grab_pics/unsplash/nitish-meena-198784.jpg)](https://unsplash.com/photos/IFh4o-U-BGg)

1. What positions have people with approved visas most frequently been hired for?
2. What are  the average salaries? **Hint**: check `wage_rate` field.
3. Where are the cities with the most H-1B visa employees?
4. What companies employ the most staff with H-1B visas?
5. Which attorneys have worked with the most employees who received H-1B visas?

****

**Adverse Event Reports (AERS) Data from FDA**

> ... Much like real-world health data from claims and EMRs, AE [Adverse Events] data is messy and largely unstructured. Most AEs are reported in a manual process, as doctors or patients commonly file reports over the phone or via mail. The data is often comprised of non-standardized reports about interventions used or side-effects produced. While there are coding mechanisms to describe the type of AE (e.g. rash, stomach pains, headache or aspirin etc.), coding standards vary over time and by country. The sheer volume of data makes it difficult to normalize the data at a scale that "old world" data infrastructure could manage ...
>
>-- <cite>[from the Enigma's blog](http://blog.enigma.io/the-challenge-in-analyzing-adverse-event-data/) by Kelvin Chan, Analyst </cite>

[![AERS](attn_grab_pics/unsplash/freestocks-org-126848.jpg)](https://unsplash.com/search/pills?photo=nss2eRzQwgw)


1. What is the name of the drug that in 2016 caused the biggest number of adverse events? **Hint**: explore the `DRUG` [table](https://app.enigma.io/table/us.gov.fda.aers.drug.2016).
2. What is an example of the event that was caused? **Hint**: use `primaryid` & `caseid` to link with the `Patient Outcomes` [table](https://app.enigma.io/table/us.gov.fda.aers.outc.2016) in 2016.
3. Can we trust the results? If not what context can we use?* (see a hint below).

Broader context: :tada:

+ [Freakonomics podcast: Bad Medicine](http://freakonomics.com/podcast/bad-medicine-part-2-drug-trials-and-tribulations/);
+ [OpenFDA portal](https://github.com/FDA/openfda)

## Data

Data can be browsed in Enigma public or downloaded from the source at the following links:

**Download from the source**

- [H-1B Data](https://www.foreignlaborcert.doleta.gov/performancedata.cfm)
- [FDA AERS](https://www.fda.gov/Drugs/GuidanceComplianceRegulatoryInformation/Surveillance/AdverseDrugEffects/ucm082193.htm)

**Browse in Enigma (export when needed)**

- [H-1B Data](https://app.enigma.io/search/source/us.gov.dol.oflc)
- [FDA AERS](https://app.enigma.io/search/source/us.gov.fda.aers)

## What we mean by data in context
At best, open government data allows those outside of government to put already-collected information to new purposes, understand the world better and cool analysis. At worst, mistaken assumptions can lead to an issue of translation. Open data is useful because of what it can reflect to us about our world but yet all datasets are affected by the context in which they are created. Using a dataset without understanding its context is like translating a sentence word by word - without knowing who wrote it and what type of idiomatic or cultural context they might be referencing. It’s difficult to know everything about the context of a dataset - unless you’re the person who created it - but there are some easy steps to check your own assumptions. The basics: pay attention to the details and when it doubt, ask a domain expert. Call up the government agency that produced the data. Think of it as your translation services.

### Understanding public data in context
Eight steps to checking assumptions, ensuring that data means what you think it means so that your analysis takes into account the right context.

1. **Explain the data out loud.**
  - To yourself works, but to someone else is better. They might have a question you haven’t thought of.
  - Tell yourself (or someone else) what does this data represent? The more specific, the better.
2. **Review a sample of the data.**
  - Pull out the fields you’re thinking of using.
  - Explain the fields to yourself, is it clear what they represent? Try rewording.
  - Is there a data dictionary that explains what these fields represent? Read it. Are the “explanations” for the columns just a vague sounding column title? Jump to step 8.
  - Examine each of these. Do the values match what you expect?
3. **Hunt down code definitions.**
  - Do some of the columns you’re thinking of contain categorical codes or anything else not immediately obvious what it represents? If so, does the data dictionary contain definitions for said codes? If not, jump to step 8.
4. **Check your summary stats.**
  - For categorical columns, what’s the most frequently occurring value? For date fields, what’s the range of the dates? Check each column you’re thinking of using. Do these values make sense with what you would expect?
  - Some domain knowledge is valuable: e.g. a given record value is usually accompanied by a set of others “domain related” values.
  - Check suspicious values against the excellent [Quartz Bad Data Guide](https://github.com/Quartz/bad-data-guide). This guide also contains plenty of other kinds of oddities to check against.
5. **Understand missing values.**
  - In step 4, did you encounter columns with suspicious low fill rate, or no data at all?
  - Check yourself that you can explain, how are missing values represented in the data? Are there different types of missing values?
6. **Understanding the system that produces the data.**
  - Can you explain the system that produces that data? If not, who can help you understand this?
7. **Look for documentation on the system that produces the data.**
  - Data dictionaries are often not as complete as a user of the data would like, but you may be able to find field documentation if you example the source of the data itself.
  - For example, the Internal Revenue Service produces only limited documentation with the (very interesting) datasets they produce. These datasets are the result of forms they put out though. Well, what is very well documented from the IRS? Instructions on how to fill out forms. Put these to use to get to the bottom of what a vague field name represents.
8. **Finally, ask the source!**
  - Don’t bring assumptions into your work, ask.
  - Use the data source as translator, people who can let you know what an idiom means or how to best join two tables together.
  - If you can’t find the precise owner, ask someone else who has used the data if they have a contact inside who can help you.
  - Or call the agency mainline and be nice and clear and persistent until you get transferred to the right person.
  - Generally when you ask, people are helpful. You’re putting their efforts to work.
