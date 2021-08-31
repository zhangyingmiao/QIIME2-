# QIIME2-
实例数据
(qiime2-2018.6) qiime2@qiime2core2018-6:~$ Select seq LC428294.1Escherichia coli
bash: Select: command not found
(qiime2-2018.6) qiime2@qiime2core2018-6:~$ clean
bash: clean: command not found
(qiime2-2018.6) qiime2@qiime2core2018-6:~$ clear

(qiime2-2018.6) qiime2@qiime2core2018-6:~$ mkdir moving-pictures
mkdir: cannot create directory ‘moving-pictures’: File exists
(qiime2-2018.6) qiime2@qiime2core2018-6:~$ cd moving-pictures
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ mkdir -p emp-single-end-sequences
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ # 3.6M
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ wget \
>   -O "emp-single-end-sequences/barcodes.fastq.gz" \
>   "https://data.qiime2.org/2021.2/tutorials/moving-pictures/emp-single-end-sequences/barcodes.fastq.gz"
--2021-08-31 12:21:04--  https://data.qiime2.org/2021.2/tutorials/moving-pictures/emp-single-end-sequences/barcodes.fastq.gz
Resolving data.qiime2.org... 54.200.1.12
Connecting to data.qiime2.org|54.200.1.12|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://s3-us-west-2.amazonaws.com/qiime2-data/2021.2/tutorials/moving-pictures/emp-single-end-sequences/barcodes.fastq.gz [following]
--2021-08-31 12:21:12--  https://s3-us-west-2.amazonaws.com/qiime2-data/2021.2/tutorials/moving-pictures/emp-single-end-sequences/barcodes.fastq.gz
Resolving s3-us-west-2.amazonaws.com... 52.218.182.72
Connecting to s3-us-west-2.amazonaws.com|52.218.182.72|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3783785 (3.6M) [application/x-gzip]
Saving to: ‘emp-single-end-sequences/barcodes.fastq.gz’

emp-single-end-sequences/barcodes.f  70%[=============================================>                    ]   2.54M  23.1KB/s    in 2m 9s   

2021-08-31 12:23:26 (20.2 KB/s) - Read error at byte 2662031/3783785 (Connection reset by peer). Retrying.

--2021-08-31 12:23:27--  (try: 2)  https://s3-us-west-2.amazonaws.com/qiime2-data/2021.2/tutorials/moving-pictures/emp-single-end-sequences/barcodes.fastq.gz
Connecting to s3-us-west-2.amazonaws.com|52.218.182.72|:443... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 3783785 (3.6M), 1121754 (1.1M) remaining [application/x-gzip]
Saving to: ‘emp-single-end-sequences/barcodes.fastq.gz’

emp-single-end-sequences/barcodes.f 100%[++++++++++++++++++++++++++++++++++++++++++++++===================>]   3.61M   350KB/s    in 3.1s    

2021-08-31 12:23:34 (350 KB/s) - ‘emp-single-end-sequences/barcodes.fastq.gz’ saved [3783785/3783785]

(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ # 24M
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ wget \
>   -O "emp-single-end-sequences/sequences.fastq.gz" \
>   "https://data.qiime2.org/2021.2/tutorials/moving-pictures/emp-single-end-sequences/sequences.fastq.gz"
--2021-08-31 12:23:52--  https://data.qiime2.org/2021.2/tutorials/moving-pictures/emp-single-end-sequences/sequences.fastq.gz
Resolving data.qiime2.org... 54.200.1.12
Connecting to data.qiime2.org|54.200.1.12|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://s3-us-west-2.amazonaws.com/qiime2-data/2021.2/tutorials/moving-pictures/emp-single-end-sequences/sequences.fastq.gz [following]
--2021-08-31 12:23:54--  https://s3-us-west-2.amazonaws.com/qiime2-data/2021.2/tutorials/moving-pictures/emp-single-end-sequences/sequences.fastq.gz
Resolving s3-us-west-2.amazonaws.com... 52.218.251.56
Connecting to s3-us-west-2.amazonaws.com|52.218.251.56|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25303756 (24M) [binary/octet-stream]
Saving to: ‘emp-single-end-sequences/sequences.fastq.gz’

emp-single-end-sequences/sequences. 100%[=================================================================>]  24.13M  1.64MB/s    in 18s     

2021-08-31 12:24:13 (1.36 MB/s) - ‘emp-single-end-sequences/sequences.fastq.gz’ saved [25303756/25303756]

(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime tools import \
>   --type EMPSingleEndSequences \
>   --input-path emp-single-end-sequences \
>   --output-path emp-single-end-sequences.qza

real	0m52.072s
user	0m19.124s
sys	0m2.876s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime demux emp-single \
>   --i-seqs emp-single-end-sequences.qza \
>   --m-barcodes-file sample-metadata.tsv \
>   --m-barcodes-column barcode-sequence \
>   --o-per-sample-sequences demux.qza \
> clear
Usage: qiime demux emp-single [OPTIONS]

Error: Got unexpected extra argument (clear)

real	0m1.037s
user	0m0.880s
sys	0m0.024s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime demux emp-single \
>   --i-seqs emp-single-end-sequences.qza \
>   --m-barcodes-file sample-metadata.tsv \
>   --m-barcodes-column barcode-sequence \
>   --o-per-sample-sequences demux.qza \
>   --o-error-correction-details demux-details.qza
Error: no such option: --o-error-correction-details

real	0m0.933s
user	0m0.844s
sys	0m0.028s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime demux emp-single \
>   --i-seqs emp-single-end-sequences.qza \
>   --m-barcodes-file sample-metadata.tsv \
>   --m-barcodes-column barcode-sequence \
>   --o-per-sample-sequences demux.qza \
> 
Saved SampleData[SequencesWithQuality] to: demux.qza

real	1m56.359s
user	1m54.476s
sys	0m0.928s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime demux summarize \
>   --i-data demux.qza \
>   --o-visualization demux.qzv
Saved Visualization to: demux.qzv

real	1m0.032s
user	0m58.476s
sys	0m0.980s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime dada2 denoise-single \
>   --i-demultiplexed-seqs demux.qza \
>   --p-trim-left 0 \
>   --p-trunc-len 120 \
>   --o-representative-sequences rep-seqs-dada2.qza \
>   --o-table table-dada2.qza \
>   --o-denoising-stats stats-dada2.qza
Saved FeatureTable[Frequency] to: table-dada2.qza
Saved FeatureData[Sequence] to: rep-seqs-dada2.qza
Saved SampleData[DADA2Stats] to: stats-dada2.qza

real	11m32.312s
user	11m22.824s
sys	0m2.124s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ qiime metadata tabulate \
>   --m-input-file stats-dada2.qza \
>   --o-visualization stats-dada2.qzv
Saved Visualization to: stats-dada2.qzv
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ mv rep-seqs-dada2.qza rep-seqs.qza
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ mv table-dada2.qza table.qza
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime phylogeny align-to-tree-mafft-fasttree \
>   --i-sequences rep-seqs.qza \
>   --o-alignment aligned-rep-seqs.qza \
>   --o-masked-alignment masked-aligned-rep-seqs.qza \
>   --o-tree unrooted-tree.qza \
>   --o-rooted-tree rooted-tree.qza
Error: QIIME 2 plugin 'phylogeny' has no action 'align-to-tree-mafft-fasttree'.

real	0m0.919s
user	0m0.828s
sys	0m0.044s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ time qiime diversity core-metrics-phylogenetic \
>   --i-phylogeny rooted-tree.qza \
>   --i-table table.qza \
>   --p-sampling-depth 1103 \
>   --m-metadata-file sample-metadata.tsv \
>   --output-dir core-metrics-results
Usage: qiime diversity core-metrics-phylogenetic [OPTIONS]

Error: Invalid value for "--i-phylogeny": Path "rooted-tree.qza" does not exist.

real	0m0.938s
user	0m0.860s
sys	0m0.016s
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ from qiime2.plugins import phylogeny
from: can't read /var/mail/qiime2.plugins
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ from qiime2.plugins.phylogeny.pipelines import align_to_tree_mafft_fasttree
from: can't read /var/mail/qiime2.plugins.phylogeny.pipelines
(qiime2-2018.6) qiime2@qiime2core2018-6:~/moving-pictures$ 
