<img width="494" height="134" alt="eeeex" src="https://github.com/user-attachments/assets/443f20ce-2b88-49ca-958c-c61262ef3bbe" />

<br/>


#

esdb tests how models classify incidents, connect endpoint events, classify network flows and apply authorization policies to evidence.

v0.3 has 9,143 cases and 13,773 questions across four assessments. development and calibration results are available below. final test has not been evaluated.

| assessment | cases | task |
|---|---:|---|
| incident classification | 1,487 | predict the provider's incident grade from guide alert metadata |
| endpoint investigation | 669 | connect process events and cite supporting events; 414 investigation cases and 255 extraction diagnostics |
| network classification | 3,263 | classify flows and make separate firewall-rule decisions |
| authorization policy | 3,724 | apply supplied policies to source programs, access requests and file-upload requests |

related cases stay in the same partition. a case is correct only when all required answers are correct. failed, missing and invalid answers count as incorrect. endpoint extraction diagnostics are excluded from the primary score.

## results

calibration case accuracy:

| assessment | jev | sev | majority |
|---|---:|---:|---:|
| incident classification | 21.82% | 21.41% | 55.15% |
| endpoint investigation | 62.16% | 30.41% | 45.95% |
| authorization policy | 84.42% | 47.97% | 28.57% |

random forest reached 59.39% on incident classification. network results are reported separately by source. jev missed 198 of 200 malicious ctu flows and 53 of 56 malicious iot flows.

## files

- [benchmark overview](docs/benchmark.md): tasks, scoring, sources, coverage limits and local build instructions.
- [calibration results](results/calibration-v0.3.json): counts, model versions, baselines, source terms and file hashes.
- [benchmark implementation](https://github.com/tensor-ac/decision-index/tree/1457a87c66c3f473b6021df68369b8f2b608572e/decision_index/cyber): build and scoring code in the decision index proposal branch.
- [decision index proposal](https://github.com/apolinario/decision-index/pull/57): the proposed integration.

## data and reproduction

this repository is the standalone home for esdb documentation and aggregate results. the implementation currently lives in `tensor-ac/decision-index`.

the full dataset is not available for public download. building it requires the local source collection and analysis records described in the [build instructions](docs/benchmark.md#local-reproduction). source-program redistribution permissions remain unresolved. source datasets have their own terms, recorded in the calibration report.

case counts do not represent independent incidents. the workplace requests were written for this benchmark. ctu and iot share a laboratory; the cse-cic-ids2018 test data adds one campaign from another publisher. public-source pretraining overlap is unknown.

## license

see [license](LICENSE). documentation adapted from the decision index proposal retains the original license notice. dataset terms are separate from the repository license.
