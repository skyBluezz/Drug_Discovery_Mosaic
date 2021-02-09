# Drug_discvovery_pipeline
Model drug id to target (mechanism of action) using 1-D convolution and timestamped sequencing


<h4> Problem statement </h4>
Years ago, therapeutic drugs were derived from  natural  remedies  in  which  the  biological mechanisms  were  not  truly  understood.  Even more recently, popular drugs such as paracetamol,  or  commonly  known  as  Acetaminophen, have been clinically established decades beforetheir  mechanisms  were  understood.  With  the emergence  of  powerful  technologies,  we  are able  to  harness  gene  expression  and  cell  viability  data.  This  data  can  plausibly  be  usedto  measure  patients  cellular  and  genomic  responses,  giving  us  an  indication  of  possible Mechanisms  of  Action  (MoA)  that  may  ex-plain the underlying process in which the drug works. This targeted method may also provide us  knowledge  of  the  pathology  of  a  given disease. With this framework, researchers may identify relevant protein targets associated witha certain disease, and be able to modulate this protein target.
<h4> Data Descrioption</h4>
Our   data   comes   from   a   new   technology  that  simultaneously  measures  cellular  responses  from  a  pool  of  100  cell  types,  distributed as a part of a Kaggle competition [1].By  pooling  different  cell  types,  we  eliminate the  need  to  identify  exante–that  is–having  to identify  which  cells  are  better  suited  for  agiven  drug.  Our  training  data  (see  Figure  1a)is a (23814, 876) frame of data, giving 23,814 samples  where  a  dish  of  cells  is  treated  witha  drug.  For  each  of  these  samples  we  have gene  expression  data  (g-0..  ,  g-771)  and  cell viability data (c-0,c-99) telling us the degradation across the 100 different cell lines. We have approximately 2,700 drugs, each of which with6 samples that correspond to different dosages and  treatment  duration  times.  Thus,  with  two dosages (D1, D2) and three treatment durations(24,48,72  hrs)  we  have  6  sample  pertubations for each drug. 
<br />

<h4> Methodlogy</h4>
The  data  offers  some  problems  however, with   high   variance   of   many   features   evenwithin  the  control  group,  or  being  tested  bythe  same  drug  (see  Figure  2a).  For  example,if  we  take  all  the  samples  associated  with  a particular drug, we find surprisingly high variance for many genes and cell viability markers, indicating  high noise  and  randomness  due  to experimentation.


We  attempt  to  reconcile  this  by  collapsing  all samples of a specific drug into a single (1,876)vector.  If  a  drug  originally  has  6  samples,  weconvert this drugs data from (6,876) to (1,876). We  introduce  convolution  to  collapse  this  dimension; we learn filters (6x1) for each feature(g-1,g-2... c-99, c-100) in order to more deeply comprehend  relationships  between  samples  ofthe same drug, collapsing the dimension of the6 dosage and treatment times.

