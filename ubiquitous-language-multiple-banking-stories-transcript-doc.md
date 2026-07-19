# Consumer Account Onboarding — Ubiquitous Language

## Source stories
> *What this is:* the domain stories this glossary was derived from. The drift and glossary tables below reference these by name.

1. [Branch Account Application Submission](../story-branch-account-application-submission.md)
2. [Compliance Kyc Review](../story-compliance-kyc-review.md)
3. [Core Banking Account Opening](../story-core-banking-account-opening.md)
4. [Digital Account Application Submission](../story-digital-account-application-submission.md)
5. [Escalation Of Stalled Kyc Cases](../story-escalation-of-stalled-kyc-cases.md)
6. [Fraud Risk Scoring](../story-fraud-risk-scoring.md)
7. [Post Account Fraud Reversal](../story-post-account-fraud-reversal.md)

## Bounded contexts
> *What this is:* a quick legend for the context labels (C1, C1a, …) used in the tables below. A **bounded context** is a boundary inside which the domain language stays consistent.

| Context | Name | What it is |
|---|---|---|
| C1 | Branch Channel | Front-office branch operations where Personal Bankers interact with Applicants, collect documents, and submit applications. |
| C2 | Digital Channel | Digital/mobile app channel where Applicants self-serve to fill in details and submit cases for account opening. |
| C3 | Compliance | Mid-office compliance operations including KYC review, watchlist screening, and identity verification. |
| C4 | Fraud | Fraud risk assessment operations including risk scoring, threshold comparison, and manual override queue. |
| C5 | Core Banking | Core banking system responsible for creating deposit accounts, ledger records, and publishing account-opened events. |
| C6 | Notification | Notification service responsible for sending communications (emails) to applicants. |

## 1. Global glossary

> *What this is:* the **global glossary** — one canonical term per real-world concept, with every observed alias preserved verbatim. This is the shared language the whole domain should converge on.<br>*The **Kind** column means:* **person** = a human role/actor; **group** = a team/department; **system** = a software system or automated component; **work object** = a document/artefact/data that flows; **event** = a signal/trigger. It separates the *people* from the *systems* from the *things they act on*.

| Concept | Canonical term | Kind | Definition | Owning context | Aliases | Appears in | Stories |
|---|---|---|---|---|---|---|---|
| personal_banker | Personal Banker | Person | A bank employee who collects applicant information, keys applications, and interacts with customers in the branch channel. | Branch Channel | Personal Banker | Branch Channel, Compliance, Fraud, Core Banking | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| applicant | Applicant | Person | A person applying to open a deposit account, providing personal details, ID, SSN, proof of address, and initial deposit. | Branch Channel | Applicant | Branch Channel, Digital Channel, Compliance, Fraud, Core Banking, Notification | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| compliance_analyst | Compliance Analyst | Person | A compliance team member who reviews screening results, documents KYC Cases, holds cases for fraud review, and approves cases. | Compliance | Compliance Analyst | Compliance, Fraud | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| compliance_ops_lead | Compliance Ops Lead | Person | A senior compliance team member who pulls stalled KYC Cases, compares risk scores against thresholds, and releases cases back for approval. | Compliance | Compliance Ops Lead | Compliance, Fraud | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| fraud_analyst | Fraud Analyst | Person | A fraud team member who monitors risk scores, compares them against thresholds, places cases into manual override queue, and can freeze/close deposit accounts. | Fraud | Fraud Analyst | Fraud, Core Banking | Branch Account Application Submission, Digital Account Application Submission, Fraud Risk Scoring, Post Account Fraud Reversal |
| core_banking_ops_analyst | Core Banking Ops Analyst | Person | A core banking operations team member who may create deposit accounts in the Core Banking System. | Core Banking | Core Banking Ops Analyst | Core Banking | Branch Account Application Submission, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases |
| screening_engine | Screening Engine | System | A system that runs applicant data against watchlists and produces screening results. | Compliance | Screening Engine | Compliance | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| fraud_engine | Fraud Engine | System | A system that produces risk scores for KYC Cases or Applications flagged for unusual funding. | Fraud | Fraud Engine | Fraud | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| core_banking_system | Core Banking System | System | The central banking system that creates deposit accounts, generates ledger records, and publishes account-opened events. | Core Banking | Core Banking System | Core Banking | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| notification_service | Notification Service | System | A system that picks up account-opened events and sends notification emails to applicants. | Notification | Notification Service | Notification | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| branch_system | Branch System | System | The system used in the branch channel where Personal Bankers key and submit applications. | Branch Channel | Branch System | Branch Channel | Digital Account Application Submission |
| digital_app | Digital App | System | The mobile application through which Applicants self-submit their details for account opening in the digital channel. | Digital Channel | Digital App | Digital Channel | Digital Account Application Submission |
| compliance_system | Compliance System | System | The system that manages compliance workflows, converts Applications/Cases into KYC Cases, and hands them to Core Banking. | Compliance | Compliance System | Compliance | Digital Account Application Submission |
| third_party_verification_service | Third-Party Verification Service | System | An external system that performs identity verification on KYC Cases. | Compliance | Third-Party Verification Service | Compliance | Compliance Kyc Review |
| application | Application | Work object | The initial document/record containing applicant details (ID, SSN, proof of address, initial deposit) collected and submitted in the branch channel. | Branch Channel | Application, the form, application | Branch Channel, Compliance, Fraud, Core Banking | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Post Account Fraud Reversal |
| case_digital | Case | Work object | The initial document/record containing applicant details created through the Digital App in the digital channel. | Digital Channel | Case, the case | Digital Channel, Compliance | Digital Account Application Submission |
| kyc_case | KYC Case | Work object | The standardized compliance record created from an Application or Case, used for screening, fraud assessment, and approval workflow. | Compliance | KYC Case, KYC file, the file, case, K.Y.C. Case | Compliance, Fraud, Core Banking | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring |
| screening_result | Screening Result | Work object | Output from the Screening Engine indicating whether the applicant matched any watchlist entries. | Compliance | Screening Result | Compliance | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal |
| risk_score | Risk Score | Work object | A numeric value generated by the Fraud Engine indicating the likelihood of fraud for a given case. | Fraud | Risk Score | Fraud, Compliance | Branch Account Application Submission, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| risk_threshold_table | Risk Threshold Table | Work object | A reference table defining acceptable risk score cutoffs per account type, used to determine if a case can proceed. | Fraud | Risk Threshold Table | Fraud | Branch Account Application Submission, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| deposit_account | Deposit Account | Work object | The bank account record created in the Core Banking System ledger after KYC approval. | Core Banking | Deposit Account, account, New Account Record | Core Banking | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal |
| new_account_record | New Account Record | Work object | The ledger record generated in the Core Banking System when a Deposit Account is created. | Core Banking | New Account Record | Core Banking | Branch Account Application Submission, Digital Account Application Submission |
| account_opened_event | Account Opened Event | Event | An event published by the Core Banking System after a deposit account is created, consumed by the Notification Service. | Core Banking | Account Opened Event, Account Opened event | Core Banking, Notification | Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission |
| notification | Notification | Work object | An email communication sent to the Applicant regarding account opening. | Notification | Notification, Confirmation Email | Notification | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal |
| welcome_packet | Welcome Packet | Work object | A printed document given to the Applicant by the Personal Banker after account creation in the branch channel. | Branch Channel | Welcome Packet, paperwork copy | Branch Channel | Branch Account Application Submission, Digital Account Application Submission |
| watchlist | Watchlist | Work object | A reference list of subjects/entities used by the Screening Engine to check applicants against. | Compliance | Watchlist | Compliance | Digital Account Application Submission |
| manual_override_queue | Manual Override Queue | Work object | A queue where KYC Cases are placed by the Fraud Analyst when the Risk Score exceeds the threshold, for further manual review. | Fraud | manual override queue | Fraud | Fraud Risk Scoring |

## 2. Concept relationships

> *What this is:* the **domain structure** — how concepts actually relate to one another (a work object is *produced by* a system, *transformed into* another, *sent to* a downstream context). This is the connective tissue the flat glossary cannot show: read down it to trace how work flows through the domain, and which concepts sit at the busy crossroads.

| From | Relationship | To | Note | Stories |
|---|---|---|---|---|
| Personal Banker | produces | Application | Personal Banker collects, keys, and submits the Application. | Branch Account Application Submission, Core Banking Account Opening, Post Account Fraud Reversal |
| Applicant | produces | Case | Applicant fills in the Case into the Digital App. | Digital Account Application Submission |
| Digital App | produces | Case | Digital App submits the Case to the Compliance System. | Digital Account Application Submission |
| Application | transformed into | KYC Case | The Application is converted into a KYC Case at the point of submission to the Screening Engine or Compliance System. | Compliance Kyc Review, Digital Account Application Submission |
| Case | transformed into | KYC Case | The Case from the Digital App is converted into a KYC Case by the Compliance System. | Digital Account Application Submission |
| Screening Engine | produces | Screening Result | Screening Engine runs the Subject against the Watchlist and produces a Screening Result. | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal |
| Screening Result | depends on | KYC Case | Screening Result is reviewed by Compliance Analyst and documented on the KYC Case. | Branch Account Application Submission, Escalation Of Stalled Kyc Cases |
| Compliance Analyst | produces | KYC Case | Compliance Analyst documents, holds, sends, and approves the KYC Case. | Branch Account Application Submission, Compliance Kyc Review, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring |
| Fraud Engine | produces | Risk Score | Fraud Engine produces a Risk Score for a KYC Case or Application. | Branch Account Application Submission, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| Risk Score | compared against | Risk Threshold Table | Risk Score is compared against the Risk Threshold Table by the Fraud Analyst or Compliance Ops Lead. | Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring, Post Account Fraud Reversal |
| Fraud Analyst | produces | Manual Override Queue | Fraud Analyst places KYC Case into the manual override queue if Risk Score exceeds threshold. | Fraud Risk Scoring |
| Compliance Ops Lead | produces | KYC Case | Compliance Ops Lead pulls stalled KYC Cases and releases them back to Compliance Analyst. | Branch Account Application Submission, Digital Account Application Submission, Escalation Of Stalled Kyc Cases |
| KYC Case | sent to | Core Banking System | KYC Case is handed to Core Banking System after approval for account creation. | Branch Account Application Submission, Compliance Kyc Review, Digital Account Application Submission, Escalation Of Stalled Kyc Cases |
| Core Banking System | produces | Deposit Account | Core Banking System creates the Deposit Account in the ledger. | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal |
| Core Banking System | produces | New Account Record | Core Banking System generates a New Account Record in the ledger. | Branch Account Application Submission, Digital Account Application Submission |
| Core Banking System | produces | Account Opened Event | Core Banking System publishes an Account Opened Event after account creation. | Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission |
| Account Opened Event | triggers | Notification Service | Notification Service picks up the Account Opened Event to send a notification. | Core Banking Account Opening |
| Notification Service | produces | Notification | Notification Service sends a Notification (email) to the Applicant. | Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal |
| Personal Banker | produces | Welcome Packet | Personal Banker prints a Welcome Packet for the Applicant. | Branch Account Application Submission, Digital Account Application Submission |
| Fraud Analyst | produces | Deposit Account | Fraud Analyst manually freezes or closes the Deposit Account in the Core Banking System. | Post Account Fraud Reversal |
| Screening Engine | depends on | Watchlist | Screening Engine runs the Subject against the Watchlist. | Digital Account Application Submission |
| Third-Party Verification Service | produces | KYC Case | Third-Party Verification Service passes and flips the KYC Case status after identity verification. | Compliance Kyc Review |
| Compliance Analyst | produces | Application | Compliance Analyst documents, holds, sends, and approves the Application (in stories where Application is used instead of KYC Case). | Core Banking Account Opening, Post Account Fraud Reversal |
| Compliance Ops Lead | monitors | Risk Score | Compliance Ops Lead compares the Risk Score against the Risk Threshold Table. | Post Account Fraud Reversal |

## 3. Context overrides

> *What this is:* where a single context uses a term that differs from the global canonical term — keep the healthy ones, fix the rest.<br>*The **Kind** column means:* **legitimate_translation** = a deliberate, healthy context-specific name to keep; **accidental_drift** = an unintended inconsistency to fix.

| Concept | Context | Local term | Global canonical | Kind | Reason |
|---|---|---|---|---|---|
| kyc_case | Core Banking | Application | KYC Case | accidental_drift | In story-core-banking-account-opening.md (Core Banking context), the work object is consistently called 'Application' even after it has been through compliance review and should be a KYC Case. This is intra-context inconsistency within the Compliance-to-Core-Banking handoff. |
| kyc_case | Fraud | Application | KYC Case | accidental_drift | In story-post-account-fraud-reversal.md, the Compliance Analyst sends an 'Application' to the Fraud Engine, but in other stories (story-fraud-risk-scoring.md) the same handoff uses 'KYC Case'. This is synonym drift within the Fraud context. |
| notification | Notification | Confirmation Email | Notification | accidental_drift | In story-core-banking-account-opening.md, the Notification Service sends a 'Confirmation Email' instead of a 'Notification'. Both refer to the same email sent to the Applicant. |

## 4. Boundary translations

> *What this is:* healthy renames that happen as a concept crosses a context boundary — the same idea, translated into each side's language. This is correct DDD, not an error.

| Concept | From context | To context | From term | To term | Note |
|---|---|---|---|---|---|
| application | Branch Channel | Compliance | Application | KYC Case | When the Application crosses from Branch Channel to Compliance, it is converted into a KYC Case — the primary compliance work object. |
| case_digital | Digital Channel | Compliance | Case | KYC Case | When the Case crosses from Digital Channel to Compliance, it is converted into a KYC Case by the Compliance System. |
| kyc_case | Compliance | Core Banking | KYC Case | Deposit Account | After approval, the KYC Case is handed to Core Banking which creates a Deposit Account — the work object changes form and ownership. |
| account_opened_event | Core Banking | Notification | Account Opened Event | Notification | The Core Banking System publishes an Account Opened Event which the Notification Service consumes to send a Notification to the Applicant. |

## 5. Homonyms

> *What this is:* a single word that means different things in different contexts — often the strongest signal that a context boundary runs straight through it.

| Term | Meanings by context | Boundary signal |
|---|---|---|
| Application | • Branch Channel — The initial document collected by the Personal Banker in the branch channel containing applicant details.<br>• Core Banking — Used incorrectly in story-core-banking-account-opening.md to refer to the compliance-reviewed work object that should be called KYC Case. | yes |
| Case | • Digital Channel — The initial document created by the Applicant through the Digital App in the digital channel.<br>• Compliance — Used as an alias/short form for KYC Case within Compliance context. | yes |

## 6. Drift report

> *What this is:* **accidental drift** — the same concept named inconsistently *within* a context, or via synonyms / typos / transcription noise. Each variant is anchored to the context that classifies it as drift AND the stories where you can fix it. Severity weights drift in a core subdomain higher than in a generic one.<br>*The **Type** column means:* **transcription_noise** = speech-to-text or typo artefacts (e.g. "item potency key"); **synonym_drift** = different words for the same meaning within one context; **intra_context_inconsistency** = a single context naming one concept several different ways; **type_drift** = the same work object categorised or typed inconsistently across stories.

| Concept | Type | Primary context | Observed variants | Canonical | Suggested fix | Subdomain | Severity | Rationale |
|---|---|---|---|---|---|---|---|---|
| kyc_case | intra_context_inconsistency | Core Banking | • Application [Core Banking] — Core Banking Account Opening<br>• KYC Case [Core Banking] — Branch Account Application Submission, Digital Account Application Submission, Escalation Of Stalled Kyc Cases | KYC Case | In story-core-banking-account-opening.md, the work object received by Core Banking System is called 'Application' but should be 'KYC Case' to match the other stories and the compliance-to-core-banking handoff. | — | high | Using 'Application' instead of 'KYC Case' in Core Banking context could lead to data model confusion — the object arriving at Core Banking has already been through compliance review and is semantically a KYC Case, not the raw Application. |
| kyc_case | intra_context_inconsistency | Fraud | • KYC Case [Fraud] — Fraud Risk Scoring, Digital Account Application Submission<br>• Application [Fraud] — Post Account Fraud Reversal | KYC Case | In story-post-account-fraud-reversal.md, the Compliance Analyst sends an 'Application' to the Fraud Engine; align with other stories by using 'KYC Case' for the object sent to fraud scoring. | — | high | Inconsistent naming of the object sent to the Fraud Engine could cause data mapping errors between Compliance and Fraud systems. |
| kyc_case | synonym_drift | Compliance | • KYC Case [Compliance] — Branch Account Application Submission, Compliance Kyc Review, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Fraud Risk Scoring<br>• K.Y.C. Case [Compliance] — Compliance Kyc Review<br>• KYC file [Compliance] — Branch Account Application Submission, Compliance Kyc Review, Digital Account Application Submission, Escalation Of Stalled Kyc Cases<br>• the file [Compliance] — Branch Account Application Submission, Compliance Kyc Review, Digital Account Application Submission, Escalation Of Stalled Kyc Cases<br>• case [Compliance] — Branch Account Application Submission, Compliance Kyc Review, Digital Account Application Submission | KYC Case | Standardise on 'KYC Case' across all Compliance stories; retire 'K.Y.C. Case', 'KYC file', 'the file', and bare 'case' as aliases. | — | medium | Multiple aliases for the same concept within Compliance could cause confusion in documentation and system design, but the core meaning is clear. |
| deposit_account | synonym_drift | Core Banking | • Deposit Account [Core Banking] — Branch Account Application Submission, Compliance Kyc Review, Core Banking Account Opening, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal<br>• New Account Record [Core Banking] — Branch Account Application Submission, Digital Account Application Submission<br>• account [Core Banking] — Branch Account Application Submission, Core Banking Account Opening, Post Account Fraud Reversal | Deposit Account | Clarify whether 'New Account Record' is the same as 'Deposit Account' or a separate ledger entry. If they are the same, standardise on 'Deposit Account'. If distinct, define both separately. | — | medium | Ambiguity between 'Deposit Account' and 'New Account Record' could lead to confusion about whether they are the same object or two different artefacts (the account vs. the ledger record). |
| notification | synonym_drift | Notification | • Notification [Notification] — Branch Account Application Submission, Compliance Kyc Review, Digital Account Application Submission, Escalation Of Stalled Kyc Cases, Post Account Fraud Reversal<br>• Confirmation Email [Notification] — Core Banking Account Opening | Notification | Standardise on 'Notification' across all stories; 'Confirmation Email' is a more specific term that can be kept as an alias but the canonical term should be consistent. | — | low | Both terms clearly refer to the same email sent to the applicant; the difference is cosmetic and unlikely to cause implementation errors. |

## 7. Open questions

> *What this is:* concepts that are ambiguous or under-specified in the source and need a domain expert to resolve.

1. What exactly triggers the hold for Fraud — is it based on the Risk Score alone or a specific threshold?
2. How does the Compliance Analyst know when the fraud hold is resolved? Is there a system handshake or manual check?
3. What is the exact status information sent back to the branch or digital systems after compliance review?
4. What triggers the Notification Service to send the notification — is it the Account Opened Event directly or some other signal?
5. How does the Compliance Ops Lead's manual pull (step 15 in story-digital-account-application-submission.md) interact with the automated handoff (step 16)?
6. What triggers the automatic escalation after five business days? (Not explicitly modeled in the chains.)
7. How does the Compliance Ops Lead decide between resolving a watchlist ambiguity versus waiting on Fraud?
8. What is the Risk Threshold Table's structure and who maintains it?
9. What exactly happens in the manual override queue after the KYC Case is placed there?
10. What are the specific threshold values for different account types?
11. What triggers the Fraud Analyst to monitor the Risk Score and initiate a freeze/closure? Is it a scheduled check or alert-based?
12. Is there any automated escalation when a Risk Score exceeds the threshold, or is it purely manual?
13. What is the role of the Core Banking Ops Analyst in the process? (Listed as an actor but rarely appears in story sequences.)
14. Is the 'New Account Record' a separate artefact from the 'Deposit Account' or the same thing described differently?
15. How does the Screening Engine convert an Application into a KYC Case — is this an automated transformation or does it require human action?